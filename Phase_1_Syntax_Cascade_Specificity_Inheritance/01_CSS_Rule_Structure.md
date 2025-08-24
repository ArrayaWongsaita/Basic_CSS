# โครงสร้าง CSS Rule: selector { property: value; }

## ภาพรวม CSS Rule

CSS Rule เป็นหน่วยพื้นฐานของการเขียน CSS ที่ประกอบด้วย 3 ส่วนหลัก:

```css
selector {
  property: value;
}
```

### องค์ประกอบของ CSS Rule

```css
/* โครงสร้างพื้นฐาน */
h1 {
  color: blue;
  font-size: 24px;
}

/* แยกส่วน:
   h1           = Selector (ตัวเลือก)
   color        = Property (คุณสมบัติ)
   blue         = Value (ค่า)
   ;            = Declaration Separator (ตัวแยก)
   { }          = Declaration Block (บล็อกคำสั่ง)
*/
```

## 1. Selector (ตัวเลือก)

Selector คือตัวกำหนดว่าจะเอาสไตล์ไปใช้กับ HTML element ไหน

### 1.1 Basic Selectors (ตัวเลือกพื้นฐาน)

#### Element Selector (เลือกตาม Tag)

```css
/* เลือก HTML tag โดยตรง */
h1 {
    color: red;
}

p {
    font-size: 16px;
}

div {
    background-color: yellow;
}

/* ใช้กับ HTML */
<h1>หัวข้อนี้จะเป็นสีแดง</h1>
<p>ย่อหน้านี้จะมีขนาด 16px</p>
<div>กล่องนี้จะเป็นพื้นหลังสีเหลือง</div>
```

#### Class Selector (เลือกตาม Class)

```css
/* เลือกตาม class attribute */
.highlight {
    background-color: yellow;
    font-weight: bold;
}

.main-title {
    font-size: 2rem;
    color: #2c3e50;
    text-align: center;
}

.btn {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

/* ใช้กับ HTML */
<p class="highlight">ข้อความเน้น</p>
<h1 class="main-title">หัวข้อหลัก</h1>
<button class="btn">ปุ่ม</button>
```

#### ID Selector (เลือกตาม ID)

```css
/* เลือกตาม id attribute */
#header {
    background-color: #2c3e50;
    color: white;
    padding: 1rem;
}

#navigation {
    display: flex;
    justify-content: space-between;
}

#footer {
    text-align: center;
    margin-top: 2rem;
}

/* ใช้กับ HTML */
<header id="header">ส่วนหัว</header>
<nav id="navigation">เมนู</nav>
<footer id="footer">ส่วนท้าย</footer>
```

#### Universal Selector (เลือกทั้งหมด)

```css
/* เลือกทุก element */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* เลือกทุก element ใน container */
.container * {
  border: 1px solid red;
}
```

### 1.2 Combination Selectors (ตัวเลือกผสม)

#### Descendant Selector (ลูกหลาน)

```css
/* เลือก p ที่อยู่ใน div */
div p {
    color: blue;
}

/* เลือก a ที่อยู่ใน nav */
nav a {
    text-decoration: none;
    color: white;
}

/* เลือก li ที่อยู่ใน ul ที่อยู่ใน nav */
nav ul li {
    list-style: none;
    display: inline-block;
}

/* HTML ที่ตรงกัน */
<div>
    <p>ข้อความนี้จะเป็นสีน้ำเงิน</p>
    <section>
        <p>ข้อความนี้ก็จะเป็นสีน้ำเงินเหมือนกัน</p>
    </section>
</div>
```

#### Child Selector (ลูกโดยตรง)

```css
/* เลือกเฉพาะ p ที่เป็นลูกโดยตรงของ div */
div > p {
    font-weight: bold;
}

/* เลือกเฉพาะ li ที่เป็นลูกโดยตรงของ ul */
ul > li {
    margin: 5px 0;
}

/* HTML ที่ตรงกัน */
<div>
    <p>ข้อความนี้จะเป็นตัวหนา (ลูกโดยตรง)</p>
    <section>
        <p>ข้อความนี้จะไม่เป็นตัวหนา (ลูกหลาน)</p>
    </section>
</div>
```

#### Multiple Selectors (หลายตัวเลือก)

```css
/* ใช้สไตล์เดียวกันกับหลาย selector */
h1,
h2,
h3 {
  color: #2c3e50;
  font-family: 'Georgia', serif;
}

.btn,
.button,
.submit {
  padding: 10px 15px;
  border-radius: 3px;
  cursor: pointer;
}

#header,
#footer {
  background-color: #34495e;
  color: white;
}
```

### 1.3 Pseudo-class Selectors (สถานะพิเศษ)

```css
/* เมื่อ hover (วางเมาส์) */
a:hover {
  color: red;
  text-decoration: underline;
}

/* เมื่อ focus (โฟกัส) */
input:focus {
  border: 2px solid blue;
  outline: none;
}

/* ลูกคนแรก */
li:first-child {
  font-weight: bold;
}

/* ลูกคนสุดท้าย */
li:last-child {
  border-bottom: none;
}

/* ลูกคนที่ n */
li:nth-child(2) {
  background-color: #f0f0f0;
}

/* ลูกคนคู่ */
tr:nth-child(even) {
  background-color: #f9f9f9;
}

/* ลูกคนคี่ */
tr:nth-child(odd) {
  background-color: white;
}
```

### 1.4 Pseudo-element Selectors (องค์ประกอบเสมือน)

```css
/* ตัวอักษรแรก */
p::first-letter {
  font-size: 2em;
  font-weight: bold;
  float: left;
}

/* บรรทัดแรก */
p::first-line {
  font-weight: bold;
  color: blue;
}

/* เพิ่มเนื้อหาก่อน */
h2::before {
  content: '★ ';
  color: gold;
}

/* เพิ่มเนื้อหาหลัง */
h2::after {
  content: ' ★';
  color: gold;
}

/* เมื่อเลือกข้อความ */
::selection {
  background-color: yellow;
  color: black;
}
```

## 2. Property (คุณสมบัติ)

Property คือคุณลักษณะที่ต้องการกำหนดให้กับ element

### 2.1 Text Properties (คุณสมบัติข้อความ)

```css
.text-example {
  /* สี */
  color: #333;

  /* ฟอนต์ */
  font-family: 'Arial', sans-serif;
  font-size: 16px;
  font-weight: bold;
  font-style: italic;

  /* การจัดวาง */
  text-align: center;
  text-decoration: underline;
  text-transform: uppercase;

  /* ระยะห่าง */
  line-height: 1.5;
  letter-spacing: 2px;
  word-spacing: 5px;
}
```

### 2.2 Box Model Properties (คุณสมบัติกล่อง)

```css
.box-example {
  /* ขนาด */
  width: 300px;
  height: 200px;

  /* ระยะห่างภายใน */
  padding: 20px;
  padding-top: 10px;
  padding-right: 15px;
  padding-bottom: 10px;
  padding-left: 15px;

  /* เส้นขอบ */
  border: 2px solid #ccc;
  border-radius: 10px;

  /* ระยะห่างภายนอก */
  margin: 20px auto;
  margin-top: 30px;

  /* พื้นหลัง */
  background-color: #f0f0f0;
  background-image: url('bg.jpg');
  background-size: cover;
}
```

### 2.3 Layout Properties (คุณสมบัติการจัดวาง)

```css
.layout-example {
  /* การแสดงผล */
  display: block;
  display: inline;
  display: inline-block;
  display: flex;
  display: grid;

  /* ตำแหน่ง */
  position: relative;
  position: absolute;
  position: fixed;
  top: 10px;
  left: 20px;

  /* การลอย */
  float: left;
  float: right;
  clear: both;

  /* การซ้อน */
  z-index: 10;
}
```

## 3. Value (ค่า)

Value คือค่าที่กำหนดให้กับ property

### 3.1 ประเภทของ Value

#### Keyword Values (ค่าคำสำคัญ)

```css
.keyword-values {
  /* ค่าคำสำคัญ */
  display: block;
  position: relative;
  text-align: center;
  font-weight: bold;
  border-style: solid;
  overflow: hidden;
}
```

#### Numeric Values (ค่าตัวเลข)

```css
.numeric-values {
  /* ตัวเลขบริสุทธิ์ */
  z-index: 5;
  opacity: 0.8;

  /* ตัวเลขที่มีหน่วย */
  width: 300px;
  height: 20em;
  margin: 1rem;
  font-size: 16pt;
  border-width: 2mm;
}
```

#### Color Values (ค่าสี)

```css
.color-values {
  /* ชื่อสี */
  color: red;
  background-color: blue;

  /* Hex Code */
  color: #ff0000;
  background-color: #00ff00;

  /* RGB */
  color: rgb(255, 0, 0);
  background-color: rgb(0, 255, 0);

  /* RGBA (มีความโปร่งใส) */
  color: rgba(255, 0, 0, 0.5);
  background-color: rgba(0, 255, 0, 0.8);

  /* HSL */
  color: hsl(0, 100%, 50%);
  background-color: hsl(120, 100%, 50%);
}
```

#### String Values (ค่าข้อความ)

```css
.string-values {
  /* ข้อความใน quotes */
  font-family: 'Times New Roman', serif;
  content: 'ข้อความเพิ่มเติม';

  /* URL */
  background-image: url('images/bg.jpg');
  background-image: url('images/pattern.png');
}
```

#### Function Values (ค่าฟังก์ชัน)

```css
.function-values {
  /* ฟังก์ชันคำนวณ */
  width: calc(100% - 40px);
  height: calc(100vh - 80px);

  /* ฟังก์ชันการไล่สี */
  background: linear-gradient(45deg, red, blue);
  background: radial-gradient(circle, white, black);

  /* ฟังก์ชันเปลี่ยนแปลง */
  transform: rotate(45deg);
  transform: scale(1.2);
  transform: translate(10px, 20px);
}
```

### 3.2 หน่วยวัด (Units)

#### Absolute Units (หน่วยสัมบูรณ์)

```css
.absolute-units {
  width: 300px; /* pixels */
  height: 2in; /* inches */
  margin: 1cm; /* centimeters */
  padding: 10mm; /* millimeters */
  font-size: 12pt; /* points */
}
```

#### Relative Units (หน่วยสัมพัทธ์)

```css
.relative-units {
  /* สัมพัทธ์กับฟอนต์ */
  width: 20em; /* 20 เท่าของ font-size */
  height: 1.5rem; /* 1.5 เท่าของ root font-size */

  /* สัมพัทธ์กับ viewport */
  width: 50vw; /* 50% ของความกว้างหน้าจอ */
  height: 100vh; /* 100% ของความสูงหน้าจอ */

  /* สัมพัทธ์กับ parent */
  width: 80%; /* 80% ของ parent */
  margin: 5%; /* 5% ของ parent */
}
```

## 4. Syntax Rules (กฎการเขียน)

### 4.1 การเขียนที่ถูกต้อง

```css
/* ✅ ถูกต้อง */
h1 {
  color: red;
  font-size: 24px;
}

.my-class {
  background-color: blue;
  padding: 10px;
}

#my-id {
  margin: 0 auto;
  width: 80%;
}
```

### 4.2 ข้อผิดพลาดที่พบบ่อย

```css
/* ❌ ผิด: ขาด semicolon */
h1 {
    color: red
    font-size: 24px;
}

/* ❌ ผิด: ขาด colon */
h1 {
    color red;
    font-size: 24px;
}

/* ❌ ผิด: เว้นวรรคใน property name */
h1 {
    font size: 24px;
    back ground-color: blue;
}

/* ❌ ผิด: ใช้ quotes ผิด */
h1 {
    font-family: Times New Roman;  /* ควรใส่ quotes */
}

/* ✅ ถูกต้อง */
h1 {
    font-family: "Times New Roman", serif;
}
```

### 4.3 Best Practices (แนวปฏิบัติที่ดี)

```css
/* ✅ จัดรูปแบบที่อ่านง่าย */
.card {
  /* Layout */
  display: flex;
  flex-direction: column;
  width: 300px;
  height: 400px;

  /* Spacing */
  margin: 1rem;
  padding: 1.5rem;

  /* Visual */
  background-color: white;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);

  /* Typography */
  font-family: 'Arial', sans-serif;
  color: #333;

  /* Animation */
  transition: transform 0.3s ease;
}

/* ✅ ใช้ comments อธิบาย */
/* Card hover effect */
.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

/* ✅ จัดกลุ่ม selectors ที่เกี่ยวข้อง */
.btn,
.button,
.submit-btn {
  display: inline-block;
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  text-decoration: none;
  transition: background-color 0.3s ease;
}

/* ✅ ใช้ shorthand properties */
.shorthand-example {
  /* แทนที่จะเขียน */
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 10px;
  margin-left: 20px;

  /* ใช้ shorthand */
  margin: 10px 20px;

  /* หรือ */
  padding: 10px 15px 10px 15px; /* top right bottom left */
  padding: 10px 15px; /* vertical horizontal */
  padding: 10px; /* all sides */
}
```

## 5. ตัวอย่างการใช้งานจริง

### 5.1 Navigation Menu

```css
/* HTML: <nav class="main-nav"><ul><li><a href="#">Menu</a></li></ul></nav> */

.main-nav {
  background-color: #2c3e50;
  padding: 0;
}

.main-nav ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
}

.main-nav li {
  margin: 0;
}

.main-nav a {
  display: block;
  color: white;
  text-decoration: none;
  padding: 1rem 1.5rem;
  transition: background-color 0.3s ease;
}

.main-nav a:hover {
  background-color: #34495e;
}

.main-nav a:focus {
  background-color: #3498db;
  outline: 2px solid #fff;
}
```

### 5.2 Card Component

```css
/* HTML: <div class="card"><h3>Title</h3><p>Content</p></div> */

.card {
  /* Layout */
  display: block;
  max-width: 350px;
  margin: 1rem auto;

  /* Visual */
  background: white;
  border: 1px solid #e1e1e1;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  overflow: hidden;

  /* Animation */
  transition: all 0.3s ease;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.card h3 {
  margin: 0;
  padding: 1.5rem 1.5rem 0.5rem;
  color: #2c3e50;
  font-size: 1.25rem;
  font-weight: 600;
}

.card p {
  margin: 0;
  padding: 0 1.5rem 1.5rem;
  color: #666;
  line-height: 1.6;
}
```

### 5.3 Form Elements

```css
/* HTML: <input type="text" class="form-input" placeholder="ชื่อ"> */

.form-input {
  /* Layout */
  display: block;
  width: 100%;
  margin-bottom: 1rem;

  /* Visual */
  padding: 0.75rem 1rem;
  border: 2px solid #ddd;
  border-radius: 6px;
  background-color: white;

  /* Typography */
  font-size: 1rem;
  font-family: inherit;
  color: #333;

  /* Animation */
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
}

.form-input:focus {
  border-color: #3498db;
  box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
  outline: none;
}

.form-input::placeholder {
  color: #999;
  opacity: 1;
}
```

## 6. การ Debug และ Troubleshooting

### 6.1 เครื่องมือ Developer Tools

```css
/* ใช้ border ชั่วคราวเพื่อดูขอบเขต */
.debug * {
  border: 1px solid red !important;
}

/* ใช้ background สีต่างๆ เพื่อดู layout */
.debug-layout {
  background-color: rgba(255, 0, 0, 0.2) !important;
}
```

### 6.2 การตรวจสอบ Syntax

```css
/* ✅ ตรวจสอบ: มี semicolon ครบไหม */
.check-syntax {
  color: red; /* ✅ มี ; */
  font-size: 16px; /* ✅ มี ; */
}

/* ✅ ตรวจสอบ: มี colon ครบไหม */
.check-colon {
  color: blue; /* ✅ มี : */
  font-weight: bold; /* ✅ มี : */
}

/* ✅ ตรวจสอบ: ปิด brackets ครบไหม */
.check-brackets {
  color: green;
} /* ✅ ปิด } */
```

## สรุป

โครงสร้าง CSS Rule พื้นฐาน `selector { property: value; }` เป็นหัวใจของการเขียน CSS:

1. **Selector** = เลือก HTML element ที่ต้องการจัดสไตล์
2. **Property** = คุณสมบัติที่ต้องการเปลี่ยน
3. **Value** = ค่าที่ต้องการกำหนด

การเข้าใจโครงสร้างนี้เป็นพื้นฐานสำคัญสำหรับการเรียนรู้ CSS ขั้นสูงต่อไป รวมถึง Cascade, Specificity, และ Inheritance ในบทต่อๆ ไป
