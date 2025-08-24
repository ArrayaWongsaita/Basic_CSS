# CSS Inheritance: การสืบทอดคุณสมบัติ

## ภาพรวม CSS Inheritance

CSS Inheritance คือกลไกที่ element ลูกจะรับคุณสมบัติบางอย่างจาก element แม่โดยอัตโนมัติ โดยไม่ต้องกำหนดซ้ำ ช่วยลดความซ้ำซ้อนในการเขียน CSS และทำให้การจัดการสไตล์เป็นระบบมากขึ้น

```html
<!-- ตัวอย่างพื้นฐาน -->
<div class="parent">
  <p class="child">ข้อความนี้จะสืบทอดคุณสมบัติจาก parent</p>
</div>
```

```css
.parent {
  color: blue; /* จะสืบทอดไปยัง child */
  font-size: 16px; /* จะสืบทอดไปยัง child */
  margin: 20px; /* จะไม่สืบทอดไปยัง child */
}

/* .child จะได้ color: blue และ font-size: 16px โดยอัตโนมัติ */
```

## 1. คุณสมบัติที่สืบทอด (Inherited Properties)

### 1.1 Text และ Font Properties

#### Color (สี)

```html
<div class="container">
  <h1>หัวข้อ</h1>
  <p>ย่อหน้า</p>
  <span>ข้อความ</span>
  <a href="#">ลิงก์</a>
</div>
```

```css
.container {
  color: #2c3e50; /* สีน้ำเงินเข้ม */
}

/* ผลลัพธ์: h1, p, span จะเป็นสี #2c3e50 */
/* ยกเว้น a ที่มีสีเริ่มต้นของเบราว์เซอร์ */
```

#### Font Properties

```css
.parent {
  /* Font properties ที่สืบทอด */
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 18px;
  font-weight: normal;
  font-style: normal;
  font-variant: normal;

  /* Line height และ letter spacing */
  line-height: 1.6;
  letter-spacing: 1px;
  word-spacing: 2px;
}

.child {
  /* ไม่ต้องกำหนดซ้ำ จะได้ค่าเดียวกับ parent */
}
```

```html
<div class="parent">
  <h2>หัวข้อ</h2>
  <!-- สืบทอด font-family, font-size เป็นต้น -->
  <p>ย่อหน้า</p>
  <!-- สืบทอด font-family, font-size เป็นต้น -->
  <ul>
    <li>รายการ 1</li>
    <!-- สืบทอด font-family, font-size เป็นต้น -->
    <li>รายการ 2</li>
  </ul>
</div>
```

#### Text Properties

```css
.document {
  /* Text properties ที่สืบทอด */
  text-align: center;
  text-transform: uppercase;
  text-decoration: none;
  text-indent: 2em;

  /* Visibility */
  visibility: visible;

  /* List properties */
  list-style-type: disc;
  list-style-position: inside;
}
```

```html
<div class="document">
  <h1>หัวข้อจะจัดกลางและตัวพิมพ์ใหญ่</h1>
  <p>ย่อหน้าจะจัดกลางและตัวพิมพ์ใหญ่</p>
  <ul>
    <li>รายการจะใช้ disc และ inside position</li>
    <li>รายการที่ 2</li>
  </ul>
</div>
```

### 1.2 ตัวอย่างการทำงานของ Font Inheritance

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        font-family: 'Arial', sans-serif;
        font-size: 16px;
        color: #333;
        line-height: 1.6;
      }

      .article {
        font-size: 18px; /* ขนาดใหม่ แต่ font-family จะสืบทอดจาก body */
      }

      .highlight {
        color: red; /* เปลี่ยนสี แต่ font-family และ font-size จะสืบทอด */
      }
    </style>
  </head>
  <body>
    <div class="article">
      <h1>หัวข้อบทความ</h1>
      <!-- font-family: Arial, font-size: 18px, color: #333 -->
      <p>เนื้อหาบทความ <span class="highlight">ข้อความเน้น</span></p>
      <!-- p: font-family: Arial, font-size: 18px, color: #333 -->
      <!-- span.highlight: font-family: Arial, font-size: 18px, color: red -->
    </div>
  </body>
</html>
```

### 1.3 Color Inheritance ในรายละเอียด

```css
/* การสืบทอดสี */
.parent {
  color: #2980b9;
}

.child {
  /* จะได้ color: #2980b9 จาก parent */
}

.grandchild {
  /* จะได้ color: #2980b9 จาก parent ผ่าน child */
}

/* ยกเว้น elements ที่มีสีเริ่มต้น */
a {
  /* ไม่สืบทอดสี เพราะ browser มีสีเริ่มต้นให้ link */
  color: inherit; /* บังคับให้สืบทอด */
}

button {
  /* ไม่สืบทอดสี เพราะ browser มีสีเริ่มต้น */
  color: inherit; /* บังคับให้สืบทอด */
}
```

```html
<div class="parent">
  <p class="child">
    ข้อความนี้เป็นสีน้ำเงิน
    <span class="grandchild">ข้อความนี้ก็เป็นสีน้ำเงิน</span>
    <a href="#">ลิงก์นี้ไม่เป็นสีน้ำเงิน (ใช้สีเริ่มต้นของ browser)</a>
    <button>ปุ่มนี้ไม่เป็นสีน้ำเงิน (ใช้สีเริ่มต้นของ browser)</button>
  </p>
</div>
```

## 2. คุณสมบัติที่ไม่สืบทอด (Non-inherited Properties)

### 2.1 Box Model Properties

#### Margin และ Padding

```html
<div class="parent">
  <div class="child">
    <div class="grandchild">เนื้อหา</div>
  </div>
</div>
```

```css
.parent {
  margin: 20px; /* ไม่สืบทอด */
  padding: 15px; /* ไม่สืบทอด */
}

.child {
  /* ไม่มี margin และ padding จาก parent */
  /* ต้องกำหนดเอง */
  margin: 10px;
  padding: 10px;
}

.grandchild {
  /* ไม่มี margin และ padding จาก parent หรือ child */
  /* จะใช้ค่าเริ่มต้น (0) */
}
```

**เหตุผลที่ไม่สืบทอด:** หากสืบทอด layout จะเสียหาย เพราะระยะห่างจะสะสมกันไปเรื่อยๆ

#### Border Properties

```css
.parent {
  border: 2px solid red; /* ไม่สืบทอด */
  border-radius: 10px; /* ไม่สืบทอด */
  border-color: blue; /* ไม่สืบทอด */
}

.child {
  /* ไม่มี border จาก parent */
  /* ต้องกำหนดเอง */
  border: 1px solid green;
}
```

#### Background Properties

```css
.parent {
  background-color: yellow; /* ไม่สืบทอด */
  background-image: url('bg.jpg'); /* ไม่สืบทอด */
  background-size: cover; /* ไม่สืบทอด */
}

.child {
  /* ไม่มี background จาก parent */
  /* พื้นหลังจะโปร่งใส (transparent) */
}
```

### 2.2 Layout Properties

#### Display และ Position

```css
.parent {
  display: flex; /* ไม่สืบทอด */
  position: relative; /* ไม่สืบทอด */
  top: 10px; /* ไม่สืบทอด */
  left: 20px; /* ไม่สืบทอด */
  z-index: 10; /* ไม่สืบทอด */
}

.child {
  /* ไม่ได้ display: flex จาก parent */
  /* จะใช้ค่าเริ่มต้น (block สำหรับ div) */
}
```

#### Float และ Clear

```css
.parent {
  float: left; /* ไม่สืบทอด */
  clear: both; /* ไม่สืบทอด */
}

.child {
  /* ไม่ float และไม่ clear */
}
```

### 2.3 ตัวอย่างเปรียบเทียบ Inherited vs Non-inherited

```html
<div class="container">
  <div class="section">
    <h2>หัวข้อ</h2>
    <p>ย่อหน้า</p>
    <div class="box">กล่องย่อย</div>
  </div>
</div>
```

```css
.container {
  /* Properties ที่สืบทอด */
  color: #2c3e50;
  font-family: 'Arial', sans-serif;
  font-size: 16px;
  line-height: 1.6;
  text-align: center;

  /* Properties ที่ไม่สืบทอด */
  margin: 20px;
  padding: 15px;
  border: 2px solid #ccc;
  background-color: #f8f9fa;
  display: flex;
  flex-direction: column;
}

/* ผลลัพธ์ที่ .section จะได้รับ: */
.section {
  /* ✅ สืบทอดมา: */
  /* color: #2c3e50; */
  /* font-family: 'Arial', sans-serif; */
  /* font-size: 16px; */
  /* line-height: 1.6; */
  /* text-align: center; */

  /* ❌ ไม่สืบทอด: */
  /* margin: 0; (ค่าเริ่มต้น) */
  /* padding: 0; (ค่าเริ่มต้น) */
  /* border: none; (ค่าเริ่มต้น) */
  /* background-color: transparent; (ค่าเริ่มต้น) */
  /* display: block; (ค่าเริ่มต้นสำหรับ div) */
}
```

## 3. การควบคุม Inheritance

### 3.1 CSS Keywords สำหรับ Inheritance

#### inherit (บังคับสืบทอด)

```css
.parent {
  margin: 20px;
  border: 2px solid red;
  background-color: yellow;
}

.child {
  /* บังคับให้สืบทอด properties ที่ปกติไม่สืบทอด */
  margin: inherit; /* จะได้ 20px */
  border: inherit; /* จะได้ 2px solid red */
  background-color: inherit; /* จะได้ yellow */
}
```

#### initial (ค่าเริ่มต้น)

```css
.parent {
  color: red;
  font-size: 20px;
}

.child {
  /* ใช้ค่าเริ่มต้นของ property แทนการสืบทอด */
  color: initial; /* จะเป็นสีดำ (ค่าเริ่มต้นของ color) */
  font-size: initial; /* จะเป็น medium (ค่าเริ่มต้นของ font-size) */
}
```

#### unset (รีเซ็ต)

```css
.parent {
  color: red;
  margin: 20px;
}

.child {
  /* ถ้า property สืบทอดได้ = inherit, ถ้าไม่ได้ = initial */
  color: unset; /* = inherit (เพราะ color สืบทอดได้) = red */
  margin: unset; /* = initial (เพราะ margin ไม่สืบทอด) = 0 */
}
```

#### revert (คืนค่า)

```css
.parent {
  color: red;
  display: flex;
}

.child {
  /* คืนค่าไปยัง user agent stylesheet */
  color: revert; /* คืนค่าไปยังสีเริ่มต้นของ browser */
  display: revert; /* คืนค่าไปยัง display เริ่มต้นของ element */
}
```

### 3.2 ตัวอย่างการใช้งาน Keywords

```html
<div class="blog">
  <article class="post">
    <h1 class="title">หัวข้อบทความ</h1>
    <p class="content">เนื้อหาบทความ</p>
    <a href="#" class="link">ลิงก์</a>
    <button class="btn">ปุ่ม</button>
  </article>
</div>
```

```css
.blog {
  color: #2c3e50;
  font-family: 'Georgia', serif;
  font-size: 18px;
  line-height: 1.8;
  margin: 20px;
  padding: 15px;
  background-color: #f8f9fa;
}

.post {
  /* สืบทอด: color, font-family, font-size, line-height */
  /* ไม่สืบทอด: margin, padding, background-color */
}

.title {
  /* สืบทอดมาจาก .blog */
  /* font-family: 'Georgia', serif; */
  /* color: #2c3e50; */

  /* Override บางคุณสมบัติ */
  font-size: 2em; /* ใหญ่กว่าที่สืบทอดมา */
  font-weight: bold;
}

.link {
  /* ปกติ link ไม่สืบทอดสี */
  color: inherit; /* บังคับให้ใช้สีจาก parent */
}

.btn {
  /* ปกติ button ไม่สืบทอดฟอนต์ */
  font-family: inherit; /* บังคับให้ใช้ฟอนต์จาก parent */
  font-size: inherit; /* บังคับให้ใช้ขนาดฟอนต์จาก parent */
  color: inherit; /* บังคับให้ใช้สีจาก parent */

  /* กำหนด properties ที่ไม่สืบทอด */
  background: none;
  border: 1px solid currentColor;
  padding: 0.5em 1em;
  cursor: pointer;
}
```

## 4. กรณีพิเศษของ Inheritance

### 4.1 Computed Values vs Specified Values

```css
.parent {
  font-size: 2em; /* ถ้า parent element มี font-size: 16px */
  /* computed value จะเป็น 32px */
}

.child {
  /* สืบทอด computed value (32px) ไม่ใช่ specified value (2em) */
  font-size: inherit; /* จะได้ 32px */
}

.grandchild {
  font-size: 1.5em; /* 1.5 × 32px = 48px */
}
```

### 4.2 Percentage Values

```css
.parent {
  font-size: 20px;
  line-height: 150%; /* computed value = 30px */
}

.child {
  /* สืบทอด computed value (30px) */
  /* line-height: 30px; */

  font-size: 16px; /* line-height ยังคงเป็น 30px */
}

/* เปรียบเทียบกับ */
.parent-unitless {
  font-size: 20px;
  line-height: 1.5; /* unitless value สืบทอดได้ */
}

.child-unitless {
  /* สืบทอด unitless value (1.5) */
  font-size: 16px; /* line-height จะเป็น 16px × 1.5 = 24px */
}
```

### 4.3 currentColor

```css
.parent {
  color: #e74c3c;
}

.child {
  /* currentColor จะใช้สีที่สืบทอดมา */
  border: 2px solid currentColor; /* border จะเป็นสี #e74c3c */
  box-shadow: 0 0 10px currentColor; /* shadow จะเป็นสี #e74c3c */
}
```

## 5. ปัญหาที่พบบ่อยและการแก้ไข

### 5.1 Links ไม่สืบทอดสี

```html
<div class="dark-theme">
  <p>ข้อความปกติ <a href="#">ลิงก์</a></p>
</div>
```

```css
.dark-theme {
  background: #2c3e50;
  color: white;
}

/* ❌ ปัญหา: link ยังเป็นสีน้ำเงินเข้ม (ไม่เห็นบนพื้นหลังเข้ม) */

/* ✅ แก้ไข: บังคับให้ link สืบทอดสี */
.dark-theme a {
  color: inherit;
}

/* หรือ */
.dark-theme a {
  color: currentColor;
}
```

### 5.2 Form Elements ไม่สืบทอดฟอนต์

```html
<div class="custom-form">
  <input type="text" placeholder="ข้อความ" />
  <textarea placeholder="ข้อความยาว"></textarea>
  <button>ส่ง</button>
</div>
```

```css
.custom-form {
  font-family: 'Roboto', sans-serif;
  font-size: 16px;
  color: #333;
}

/* ❌ ปัญหา: form elements ไม่สืบทอดฟอนต์ */

/* ✅ แก้ไข: บังคับให้สืบทอด */
.custom-form input,
.custom-form textarea,
.custom-form button {
  font-family: inherit;
  font-size: inherit;
  color: inherit;
}

/* หรือใช้ universal selector */
.custom-form * {
  font-family: inherit;
}
```

### 5.3 Table Elements และ Inheritance

```html
<div class="data-table">
  <table>
    <thead>
      <tr>
        <th>หัวข้อ</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>ข้อมูล</td>
      </tr>
    </tbody>
  </table>
</div>
```

```css
.data-table {
  font-family: 'Helvetica', sans-serif;
  color: #333;
  text-align: center;
}

/* Table elements สืบทอดฟอนต์และสี แต่อาจมี browser styles แทรก */

/* ตรวจสอบและแก้ไข */
.data-table table {
  border-collapse: collapse; /* สำคัญสำหรับ table styling */
}

.data-table th,
.data-table td {
  /* บางเบราว์เซอร์อาจมี font-weight หรือ text-align ของตัวเอง */
  font-weight: inherit;
  text-align: inherit;
}
```

## 6. Best Practices สำหรับ Inheritance

### 6.1 ตั้งค่า Base Styles

```css
/* ✅ ตั้งค่าพื้นฐานที่ html หรือ body */
html {
  font-size: 16px; /* base font size */
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  line-height: 1.6;
  color: #333;

  /* properties อื่นที่ต้องการให้สืบทอด */
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
}

/* ทุก element จะสืบทอดฟอนต์และสี */
```

### 6.2 ใช้ CSS Custom Properties กับ Inheritance

```css
:root {
  --text-color: #333;
  --font-family: 'Segoe UI', sans-serif;
  --line-height: 1.6;
}

body {
  color: var(--text-color);
  font-family: var(--font-family);
  line-height: var(--line-height);
}

/* Theme switching */
.dark-theme {
  --text-color: #fff;
}

/* ทุก element จะเปลี่ยนสีตาม theme โดยอัตโนมัติ */
```

### 6.3 จัดการ Form Elements

```css
/* ✅ Reset form elements ให้สืบทอดฟอนต์ */
input,
textarea,
select,
button {
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
  color: inherit;
}

/* หรือใช้ universal selector (ระวังผลกระทบ) */
* {
  font-family: inherit;
}
```

### 6.4 ใช้ currentColor

```css
/* ✅ ใช้ currentColor สำหรับ borders และ decorations */
.icon {
  fill: currentColor; /* SVG icon จะใช้สีเดียวกับข้อความ */
}

.button {
  border: 1px solid currentColor;
  color: #007bff; /* border จะเป็นสี #007bff ด้วย */
}

.button:hover {
  color: #0056b3; /* border จะเปลี่ยนสีตามไปด้วย */
}
```

## 7. การ Debug Inheritance

### 7.1 ใช้ Developer Tools

```css
/* ใน Developer Tools */
/* 1. คลิกขวา element -> Inspect */
/* 2. ดูแท็บ Computed ในส่วน Styles */
/* 3. ค้นหา property ที่สนใจ */
/* 4. จะเห็นว่าค่านั้นมาจาก inherited หรือไม่ */

/* ตัวอย่างใน Computed tab: */
/*
color: rgb(44, 62, 80)
├─ .parent { color: #2c3e50; } (inherited)
└─ user agent stylesheet
*/
```

### 7.2 เทคนิคการทดสอบ

```css
/* ใช้ outline เพื่อดู inheritance chain */
.debug-inheritance * {
  outline: 1px solid red;
}

/* ใช้ pseudo-elements แสดงข้อมูล */
.debug-font::before {
  content: 'Font: ' attr(data-font);
  position: absolute;
  background: yellow;
  color: black;
  font-size: 12px;
  padding: 2px;
}
```

```html
<!-- เพิ่ม attribute เพื่อ debug -->
<div class="parent debug-font" data-font="Arial 16px">
  <p class="child debug-font" data-font="inherited">ข้อความ</p>
</div>
```

### 7.3 JavaScript สำหรับ Debug

```javascript
// ดู computed styles
function checkInheritance(element, property) {
  const computed = getComputedStyle(element);
  const value = computed.getPropertyValue(property);
  console.log(`${property}: ${value}`);

  // ดู parent values
  let parent = element.parentElement;
  while (parent) {
    const parentComputed = getComputedStyle(parent);
    const parentValue = parentComputed.getPropertyValue(property);
    console.log(`Parent ${parent.tagName}: ${parentValue}`);
    parent = parent.parentElement;
  }
}

// การใช้งาน
checkInheritance(document.querySelector('.child'), 'color');
```

## สรุป

### คุณสมบัติที่สืบทอด:

- **Text/Font**: color, font-family, font-size, font-weight, line-height, text-align
- **List**: list-style-type, list-style-position
- **Table**: border-collapse, border-spacing
- **Visibility**: visibility

### คุณสมบัติที่ไม่สืบทอด:

- **Box Model**: margin, padding, border, width, height
- **Background**: background-color, background-image
- **Layout**: display, position, float, top, left
- **Transform**: transform, opacity (ส่วนใหญ่)

### การควบคุม Inheritance:

- `inherit`: บังคับสืบทอด
- `initial`: ใช้ค่าเริ่มต้น
- `unset`: รีเซ็ตตามธรรมชาติของ property
- `revert`: คืนค่าไปยัง user agent stylesheet

การเข้าใจ Inheritance ช่วยให้เขียน CSS ที่มีประสิทธิภาพ ลดความซ้ำซ้อน และง่ายต่อการบำรุงรักษา!
