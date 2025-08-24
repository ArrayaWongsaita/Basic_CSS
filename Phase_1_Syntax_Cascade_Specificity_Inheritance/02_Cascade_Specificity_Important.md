# CSS Cascade, Specificity และ !important

## ภาพรวม

CSS ย่อมาจาก **Cascading** Style Sheets ซึ่งคำว่า "Cascading" หมายถึงการไหลลงมาเหมือนน้ำตก เป็นกลไกที่เบราว์เซอร์ใช้ในการตัดสินใจว่าจะใช้สไตล์ไหนเมื่อมี CSS หลายแหล่งที่กำหนดสไตล์ให้กับ element เดียวกัน

## 1. Cascade (การไหลซ้อน)

### 1.1 แหล่งที่มาของ CSS (CSS Sources)

CSS สามารถมาจากหลายแหล่งตามลำดับความสำคัญ:

#### ลำดับความสำคัญ (จากน้อยไปมาก):

```css
/* 1. Browser Default Styles (User Agent Stylesheet) */
/* เบราว์เซอร์กำหนดให้เอง */
h1 {
  display: block;
  font-size: 2em;
  margin: 0.67em 0;
  font-weight: bold;
}

/* 2. User Styles (ผู้ใช้กำหนด) */
/* ผู้ใช้สามารถกำหนดใน browser settings */
* {
  font-size: 18px !important; /* ผู้ใช้ต้องการตัวอักษรใหญ่ */
}

/* 3. Author Styles (ผู้พัฒนากำหนด) */
/* CSS ที่เราเขียน */
h1 {
  color: blue;
  font-size: 24px;
}
```

### 1.2 ลำดับการประมวลผล CSS

```html
<!-- HTML -->
<!DOCTYPE html>
<html>
  <head>
    <!-- 1. External CSS (แรกสุด) -->
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="main.css" />

    <!-- 2. Internal CSS (ถัดมา) -->
    <style>
      h1 {
        color: green;
      }
    </style>
  </head>
  <body>
    <!-- 3. Inline CSS (สุดท้าย - สำคัญที่สุด) -->
    <h1 style="color: red;">หัวข้อ</h1>
  </body>
</html>
```

**ผลลัพธ์:** หัวข้อจะเป็น**สีแดง** (inline CSS ชนะ)

### 1.3 กฎ Last Rule Wins

เมื่อ specificity เท่ากัน กฎที่เขียนทีหลังจะชนะ:

```css
/* ไฟล์ main.css */
h1 {
  color: blue;
} /* กฎแรก */
h1 {
  color: green;
} /* กฎสอง - จะชนะ */

.title {
  color: red;
} /* กฎสาม */
.title {
  color: yellow;
} /* กฎสี่ - จะชนะ */
```

```html
<!-- HTML -->
<h1 class="title">หัวข้อ</h1>
<!-- ผลลัพธ์: เป็นสีเหลือง (class มี specificity สูงกว่า element) -->
```

## 2. Specificity (ความเฉพาะเจาะจง)

Specificity เป็นระบบคะแนนที่เบราว์เซอร์ใช้ตัดสินใจว่า CSS rule ไหนควรได้รับการนำไปใช้

### 2.1 ระบบการคำนวณ Specificity

Specificity คำนวณด้วยระบบ 4 หลัก: **(a, b, c, d)**

```
a = Inline styles (style="")
b = IDs (#id)
c = Classes (.class), attributes ([attr]), pseudo-classes (:hover)
d = Elements (div, h1), pseudo-elements (::before)
```

### 2.2 ตัวอย่างการคำนวณ

```css
/* Specificity: (0, 0, 0, 1) = 1 */
h1 {
  color: blue;
}

/* Specificity: (0, 0, 1, 0) = 10 */
.title {
  color: green;
}

/* Specificity: (0, 1, 0, 0) = 100 */
#header {
  color: red;
}

/* Specificity: (1, 0, 0, 0) = 1000 */
/* <h1 style="color: yellow;">หัวข้อ</h1> */

/* Specificity: (0, 0, 1, 1) = 11 */
h1.title {
  color: purple;
}

/* Specificity: (0, 1, 1, 0) = 110 */
#header .title {
  color: orange;
}

/* Specificity: (0, 1, 2, 1) = 121 */
#header .nav .title {
  color: pink;
}
```

### 2.3 ตัวอย่างการเปรียบเทียบ Specificity

```html
<!-- HTML -->
<div id="container">
  <h1 class="main-title highlight">หัวข้อหลัก</h1>
</div>
```

```css
/* 1. Specificity: (0, 0, 0, 1) = 1 */
h1 {
  color: black;
}

/* 2. Specificity: (0, 0, 1, 0) = 10 */
.main-title {
  color: blue;
}

/* 3. Specificity: (0, 0, 1, 1) = 11 */
h1.main-title {
  color: green;
}

/* 4. Specificity: (0, 0, 2, 0) = 20 */
.main-title.highlight {
  color: orange;
}

/* 5. Specificity: (0, 1, 0, 0) = 100 */
#container {
  color: red;
}

/* 6. Specificity: (0, 1, 1, 0) = 110 */
#container .main-title {
  color: purple;
}

/* 7. Specificity: (0, 1, 2, 1) = 121 - ชนะ! */
#container h1.main-title.highlight {
  color: yellow;
}
```

**ผลลัพธ์:** หัวข้อจะเป็น**สีเหลือง** (specificity สูงสุด)

### 2.4 ลำดับความสำคัญ: inline > id > class > element

#### 2.4.1 Inline Styles (สูงสุด)

```html
<!-- Specificity: (1, 0, 0, 0) = 1000 -->
<h1 style="color: red;">หัวข้อ</h1>
```

```css
/* แม้จะมี ID ก็แพ้ inline */
#header h1.title.highlight {
  color: blue;
} /* (0, 1, 2, 1) = 121 */
```

#### 2.4.2 ID Selectors

```css
/* Specificity: (0, 1, 0, 0) = 100 */
#main-header {
  color: blue;
}

/* Specificity: (0, 2, 0, 0) = 200 */
#container #main-header {
  color: green;
}

/* Specificity: (0, 1, 1, 1) = 111 */
#main-header h1.title {
  color: purple;
}
```

#### 2.4.3 Class, Attribute, และ Pseudo-class Selectors

```css
/* Classes: (0, 0, 1, 0) = 10 */
.title {
  color: red;
}
.highlight {
  color: blue;
}

/* Attributes: (0, 0, 1, 0) = 10 */
[data-type='header'] {
  color: green;
}

/* Pseudo-classes: (0, 0, 1, 0) = 10 */
:hover {
  color: orange;
}
:nth-child(2) {
  color: purple;
}

/* รวมกัน: (0, 0, 3, 0) = 30 */
.title.highlight:hover {
  color: pink;
}
```

#### 2.4.4 Element และ Pseudo-element Selectors (ต่ำสุด)

```css
/* Elements: (0, 0, 0, 1) = 1 */
h1 {
  color: black;
}
div {
  color: gray;
}

/* Pseudo-elements: (0, 0, 0, 1) = 1 */
::before {
  color: blue;
}
::after {
  color: green;
}

/* รวมกัน: (0, 0, 0, 3) = 3 */
div h1::before {
  color: red;
}
```

### 2.5 ตัวอย่างเปรียบเทียบแบบละเอียด

```html
<!-- HTML -->
<body>
  <header id="main-header" class="site-header">
    <h1 class="logo-text highlight" data-role="title">เว็บไซต์</h1>
  </header>
</body>
```

```css
/* การเปรียบเทียบ Specificity */

/* 1. (0, 0, 0, 1) = 1 */
h1 {
  color: #000;
}

/* 2. (0, 0, 1, 0) = 10 - ชนะข้อ 1 */
.logo-text {
  color: #111;
}

/* 3. (0, 0, 1, 1) = 11 - ชนะข้อ 2 */
h1.logo-text {
  color: #222;
}

/* 4. (0, 0, 2, 0) = 20 - ชนะข้อ 3 */
.logo-text.highlight {
  color: #333;
}

/* 5. (0, 0, 1, 0) = 10 - แพ้ข้อ 4 */
[data-role='title'] {
  color: #444;
}

/* 6. (0, 0, 2, 1) = 21 - ชนะข้อ 4 */
h1.logo-text.highlight {
  color: #555;
}

/* 7. (0, 1, 0, 0) = 100 - ชนะข้อ 6 */
#main-header {
  color: #666;
}

/* 8. (0, 1, 1, 0) = 110 - ชนะข้อ 7 */
#main-header .logo-text {
  color: #777;
}

/* 9. (0, 1, 2, 1) = 121 - ชนะข้อ 8 */
#main-header h1.logo-text.highlight {
  color: #888;
}

/* 10. (1, 0, 0, 0) = 1000 - ชนะทุกอย่าง */
/* <h1 style="color: #999;">เว็บไซต์</h1> */
```

**ผลลัพธ์:** หากไม่มี inline style = สี #888, หากมี inline style = สี #999

## 3. !important (ควรหลีกเลี่ยง)

### 3.1 ความหมายของ !important

`!important` เป็นการบังคับให้ CSS property นั้นมีความสำคัญสูงสุด โดยข้ามระบบ specificity

```css
/* !important จะชนะทุกอย่าง (ยกเว้น !important อื่นที่มี specificity สูงกว่า) */
p {
  color: red !important;
}

/* แม้จะมี specificity สูงกว่า ก็ยังแพ้ !important */
#container .content p.highlight {
  color: blue;
} /* แพ้ */
```

### 3.2 การทำงานของ !important

```html
<!-- HTML -->
<div id="container">
  <p class="text highlight" style="color: green;">ข้อความ</p>
</div>
```

```css
/* 1. ปกติ inline style จะชนะ */
#container .text.highlight {
  color: blue;
} /* (0, 1, 2, 0) = 120 */
/* <p style="color: green;"> = (1, 0, 0, 0) = 1000 - ชนะ */

/* 2. แต่ !important จะชนะ inline style */
#container .text {
  color: red !important;
} /* ชนะ inline style */

/* 3. !important vs !important = ดู specificity */
.text {
  color: yellow !important;
} /* (0, 0, 1, 0) */
#container .text {
  color: purple !important;
} /* (0, 1, 1, 0) - ชนะ */
```

### 3.3 เหตุผลที่ควรหลีกเลี่ยง !important

#### 3.3.1 ทำลายระบบ Cascade

```css
/* ❌ ปัญหา: ใช้ !important มากเกินไป */
.button {
  background: blue !important;
  color: white !important;
  padding: 10px !important;
}

.button-primary {
  background: red !important; /* ต้องใช้ !important เพื่อ override */
}

.button-large {
  padding: 20px !important; /* ต้องใช้ !important เพื่อ override */
}

/* ❌ ปัญหา: ไม่สามารถ override ได้ง่าย */
.special-button {
  background: green; /* จะไม่ทำงาน เพราะแพ้ !important */
}
```

#### 3.3.2 ยากต่อการ Debug

```css
/* ❌ ยากหาสาเหตุว่าทำไมสีไม่เปลี่ยน */
.header {
  color: blue !important;
}

/* ที่ไหนสักแห่งในไฟล์อื่น */
.header {
  color: red;
} /* ไม่ทำงาน แต่ไม่รู้เหตุผล */
```

#### 3.3.3 ยากต่อการบำรุงรักษา

```css
/* ❌ วงจรอุบาทว์ของ !important */
.text {
  color: blue !important;
}
.text-red {
  color: red !important;
}
.text-green {
  color: green !important;
}
.text-override {
  color: yellow !important;
}
.text-final {
  color: purple !important;
}
/* ต้องใช้ !important เรื่อยๆ เพื่อ override */
```

### 3.4 ทางเลือกที่ดีกว่า !important

#### 3.4.1 ใช้ Specificity อย่างชาญฉลาด

```css
/* ✅ ดี: ใช้ specificity แทน !important */
.button {
  background: blue;
}

/* แทนที่จะใช้ !important */
.button-primary {
  background: red !important;
}

/* ใช้ specificity สูงกว่า */
.button.button-primary {
  background: red;
}
```

#### 3.4.2 จัดระเบียบ CSS Structure

```css
/* ✅ ดี: เรียงลำดับจากทั่วไปไปเฉพาะ */

/* 1. Base styles */
.button {
  display: inline-block;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  background: #ccc;
  color: #333;
}

/* 2. Variants */
.button--primary {
  background: #007bff;
  color: white;
}
.button--danger {
  background: #dc3545;
  color: white;
}
.button--success {
  background: #28a745;
  color: white;
}

/* 3. Sizes */
.button--small {
  padding: 4px 8px;
  font-size: 0.8rem;
}
.button--large {
  padding: 12px 24px;
  font-size: 1.2rem;
}

/* 4. States */
.button:hover {
  opacity: 0.8;
}
.button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
```

#### 3.4.3 ใช้ CSS Custom Properties (Variables)

```css
/* ✅ ดี: ใช้ CSS Variables แทน !important */
:root {
  --primary-color: #007bff;
  --danger-color: #dc3545;
}

.button {
  background: var(--primary-color);
  color: white;
}

/* เปลี่ยนสีโดยไม่ต้อง override */
.danger-section {
  --primary-color: var(--danger-color);
}
```

### 3.5 กรณีที่ใช้ !important ได้

#### 3.5.1 Utility Classes

```css
/* ✅ ใช้ได้: utility classes ที่ต้องการให้แน่ใจว่าทำงาน */
.hide { display: none !important; }
.show { display: block !important; }
.text-center { text-align: center !important; }
.text-left { text-align: left !important; }
.text-right { text-align: right !important; }

/* การใช้งาน */
<div class="complex-component text-center">
    <!-- ต้องการให้จัดกลางแน่ๆ แม้จะมี CSS อื่นมาแทรก -->
</div>
```

#### 3.5.2 Override Third-party CSS

```css
/* ✅ ใช้ได้: แก้ไข CSS จาก library ภายนอกที่ไม่สามารถแก้ได้ */
/* Override Bootstrap หรือ library อื่น */
.bootstrap-component {
  margin: 0 !important; /* จำเป็นเพื่อ override Bootstrap */
}
```

#### 3.5.3 Print Styles

```css
/* ✅ ใช้ได้: print styles ที่ต้องการให้แน่ใจ */
@media print {
  .no-print {
    display: none !important;
  }
  .print-only {
    display: block !important;
  }

  /* ต้องการให้แน่ใจว่าไม่มีสีพื้นหลังตอนพิมพ์ */
  * {
    background: white !important;
    color: black !important;
  }
}
```

## 4. การ Debug Cascade และ Specificity

### 4.1 ใช้ Developer Tools

```css
/* เปิด Developer Tools (F12) */
/* 1. คลิกขวา element -> Inspect */
/* 2. ดูแท็บ Styles ทางขวา */
/* 3. ดู CSS ที่ถูกใช้และถูกข้าม (มีเส้นขีดฆ่า) */

/* ตัวอย่างที่แสดงใน DevTools */
element.style {
  color: red; /* inline style - specificity สูงสุด */
}

#header .title {
  color: blue; /* ถูกขีดฆ่า - specificity ต่ำกว่า */
}

.title {
  color: green; /* ถูกขีดฆ่า - specificity ต่ำกว่า */
}
```

### 4.2 เทคนิคการ Debug

#### 4.2.1 ใช้ Background Color เพื่อทดสอบ

```css
/* ใช้สีพื้นหลังดูว่า selector ไหนทำงาน */
.debug-1 {
  background: red !important;
}
.debug-2 {
  background: blue !important;
}
.debug-3 {
  background: green !important;
}

/* เพิ่ม class เหล่านี้ใน HTML เพื่อดูว่า element ไหนถูกเลือก */
```

#### 4.2.2 ใช้ Console เพื่อทดสอบ

```javascript
// ใน Browser Console
// ดู computed styles
getComputedStyle(document.querySelector('.title')).color;

// ดู CSS rules ที่มีผล
document.querySelector('.title').style.color;
```

#### 4.2.3 สร้าง Specificity Calculator

```css
/* คำนวณ specificity เอง */
/* #id = 100, .class = 10, element = 1 */

/* ตัวอย่าง: #header .nav .item a:hover */
/* = 100 + 10 + 10 + 1 + 10 = 131 */
```

## 5. Best Practices สำหรับ Cascade และ Specificity

### 5.1 หลีกเลี่ยง High Specificity

```css
/* ❌ หลีกเลี่ยง: specificity สูงเกินไป */
#page #header #nav ul.menu li.item a.link {
  color: blue;
}

/* ✅ ดี: ใช้ class และ specificity ต่ำ */
.nav-link {
  color: blue;
}
```

### 5.2 จัดลำดับ CSS อย่างมีระบบ

```css
/* 1. Reset/Normalize */
* {
  margin: 0;
  padding: 0;
}

/* 2. Base elements */
body {
  font-family: Arial;
}
h1,
h2,
h3 {
  color: #333;
}

/* 3. Layout */
.container {
  max-width: 1200px;
}
.grid {
  display: grid;
}

/* 4. Components */
.button {
  padding: 10px;
}
.card {
  border: 1px solid #ccc;
}

/* 5. Utilities */
.text-center {
  text-align: center;
}
.mb-1 {
  margin-bottom: 1rem;
}

/* 6. States & Modifiers */
.button:hover {
  opacity: 0.8;
}
.button--large {
  padding: 15px;
}

/* 7. Media queries */
@media (max-width: 768px) {
  .container {
    padding: 1rem;
  }
}
```

### 5.3 ใช้ Naming Convention

```css
/* BEM Methodology */
.block {
}
.block__element {
}
.block--modifier {
}

/* ตัวอย่าง */
.card {
} /* Block */
.card__header {
} /* Element */
.card__body {
} /* Element */
.card__footer {
} /* Element */
.card--large {
} /* Modifier */
.card--featured {
} /* Modifier */
```

### 5.4 ใช้ CSS Custom Properties

```css
/* ✅ ดี: ใช้ CSS Variables สำหรับความยืดหยุ่น */
:root {
  --color-primary: #007bff;
  --color-secondary: #6c757d;
  --spacing-small: 0.5rem;
  --spacing-medium: 1rem;
  --spacing-large: 2rem;
}

.button {
  background: var(--color-primary);
  padding: var(--spacing-small) var(--spacing-medium);
}

/* สามารถ override ได้ง่าย */
.dark-theme {
  --color-primary: #0056b3;
}
```

## สรุป

### Cascade

- CSS มาจากหลายแหล่ง: Browser → User → Author
- ลำดับการโหลด: External → Internal → Inline
- กฎหลัง override กฎก่อน (เมื่อ specificity เท่ากัน)

### Specificity

- ระบบคะแนน: **inline (1000) > id (100) > class (10) > element (1)**
- คำนวณเป็น 4 หลัก: (a, b, c, d)
- Specificity สูงกว่าชนะเสมอ

### !important

- **หลีกเลี่ยงการใช้** เว้นแต่จำเป็นจริงๆ
- ใช้ได้กับ: Utility classes, Override third-party CSS, Print styles
- ใช้ Specificity และ CSS structure ที่ดีแทน

การเข้าใจ Cascade และ Specificity จะช่วยให้เขียน CSS ที่คาดเดาได้ บำรุงรักษาง่าย และมีประสิทธิภาพ!
