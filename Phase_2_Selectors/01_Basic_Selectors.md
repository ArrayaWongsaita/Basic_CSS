# CSS Selectors พื้นฐาน: element, .class, #id, \*, กลุ่ม (,)

## ภาพรวม CSS Selectors

CSS Selector คือรูปแบบที่ใช้เลือก HTML elements เพื่อนำสไตล์ไปใช้ โดยเบราว์เซอร์จะค้นหา elements ที่ตรงกับ selector แล้วนำ CSS properties ไปใช้กับ elements เหล่านั้น

```css
/* โครงสร้างพื้นฐาน */
selector {
  property: value;
}
```

### ประเภทของ Basic Selectors

1. **Element Selector** - เลือกตาม HTML tag
2. **Class Selector** - เลือกตาม class attribute
3. **ID Selector** - เลือกตาม id attribute
4. **Universal Selector** - เลือกทุก element
5. **Group Selector** - เลือกหลาย selector พร้อมกัน

## 1. Element Selector (ตัวเลือกองค์ประกอบ)

### ความหมาย

Element Selector เลือก HTML elements ตามชื่อ tag โดยตรง

### รูปแบบ

```css
tagname {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### การจัดสไตล์ Headings

```html
<!-- HTML -->
<h1>หัวข้อระดับ 1</h1>
<h2>หัวข้อระดับ 2</h2>
<h3>หัวข้อระดับ 3</h3>
<h4>หัวข้อระดับ 4</h4>
<h5>หัวข้อระดับ 5</h5>
<h6>หัวข้อระดับ 6</h6>
```

```css
/* CSS */
h1 {
  font-size: 2.5rem;
  color: #2c3e50;
  text-align: center;
  margin-bottom: 1rem;
}

h2 {
  font-size: 2rem;
  color: #34495e;
  border-bottom: 2px solid #3498db;
  padding-bottom: 0.5rem;
}

h3 {
  font-size: 1.5rem;
  color: #7f8c8d;
  margin: 1rem 0 0.5rem 0;
}

h4,
h5,
h6 {
  font-size: 1.2rem;
  color: #95a5a6;
  font-weight: 600;
}
```

#### การจัดสไตล์ Text Elements

```html
<!-- HTML -->
<p>นี่คือย่อหน้าปกติ</p>
<blockquote>นี่คือข้อความที่อ้างอิง</blockquote>
<strong>ข้อความเน้น</strong>
<em>ข้อความเอียง</em>
<small>ข้อความเล็ก</small>
```

```css
/* CSS */
p {
  line-height: 1.6;
  margin-bottom: 1rem;
  color: #333;
  font-size: 1rem;
}

blockquote {
  background-color: #f8f9fa;
  border-left: 4px solid #007bff;
  padding: 1rem;
  margin: 1rem 0;
  font-style: italic;
  color: #495057;
}

strong {
  font-weight: 700;
  color: #e74c3c;
}

em {
  font-style: italic;
  color: #9b59b6;
}

small {
  font-size: 0.875rem;
  color: #6c757d;
}
```

#### การจัดสไตล์ Lists

```html
<!-- HTML -->
<ul>
  <li>รายการแบบไม่เรียงลำดับ 1</li>
  <li>รายการแบบไม่เรียงลำดับ 2</li>
  <li>รายการแบบไม่เรียงลำดับ 3</li>
</ul>

<ol>
  <li>รายการแบบเรียงลำดับ 1</li>
  <li>รายการแบบเรียงลำดับ 2</li>
  <li>รายการแบบเรียงลำดับ 3</li>
</ol>
```

```css
/* CSS */
ul {
  list-style-type: disc;
  padding-left: 2rem;
  margin-bottom: 1rem;
}

ol {
  list-style-type: decimal;
  padding-left: 2rem;
  margin-bottom: 1rem;
}

li {
  margin-bottom: 0.5rem;
  line-height: 1.5;
}
```

#### การจัดสไตล์ Links

```html
<!-- HTML -->
<a href="https://example.com">ลิงก์ภายนอก</a>
<a href="#section1">ลิงก์ภายใน</a>
<a href="mailto:email@example.com">ลิงก์อีเมล</a>
```

```css
/* CSS */
a {
  color: #007bff;
  text-decoration: none;
  transition: color 0.3s ease;
}

a:hover {
  color: #0056b3;
  text-decoration: underline;
}

a:visited {
  color: #6f42c1;
}

a:active {
  color: #e83e8c;
}
```

### ข้อดีและข้อเสียของ Element Selector

#### ✅ ข้อดี

- **เขียนง่าย**: ไม่ต้องเพิ่ม class หรือ id
- **ใช้ได้ทันที**: ไม่ต้องแก้ไข HTML
- **เหมาะสำหรับ base styles**: การตั้งค่าพื้นฐาน

#### ❌ ข้อเสีย

- **ไม่เฉพาะเจาะจง**: ส่งผลกับ element ทุกตัวในหน้า
- **ยากต่อการควบคุม**: ไม่สามารถเลือกเฉพาะบางตัวได้
- **Specificity ต่ำ**: แพ้ class และ id selector

## 2. Class Selector (ตัวเลือกคลาส)

### ความหมาย

Class Selector เลือก elements ที่มี class attribute ตรงกัน โดยใช้เครื่องหมาย `.` นำหน้า

### รูปแบบ

```css
.classname {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### Button Components

```html
<!-- HTML -->
<button class="btn">ปุ่มปกติ</button>
<button class="btn-primary">ปุ่มหลัก</button>
<button class="btn-secondary">ปุ่มรอง</button>
<button class="btn-success">ปุ่มสำเร็จ</button>
<button class="btn-danger">ปุ่มอันตราย</button>
<button class="btn-warning">ปุ่มเตือน</button>
```

```css
/* CSS */
.btn {
  display: inline-block;
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  font-weight: 400;
  text-align: center;
  border: 1px solid transparent;
  border-radius: 0.375rem;
  cursor: pointer;
  transition: all 0.3s ease;
  text-decoration: none;
}

.btn-primary {
  background-color: #007bff;
  border-color: #007bff;
  color: white;
}

.btn-primary:hover {
  background-color: #0056b3;
  border-color: #004085;
}

.btn-secondary {
  background-color: #6c757d;
  border-color: #6c757d;
  color: white;
}

.btn-success {
  background-color: #28a745;
  border-color: #28a745;
  color: white;
}

.btn-danger {
  background-color: #dc3545;
  border-color: #dc3545;
  color: white;
}

.btn-warning {
  background-color: #ffc107;
  border-color: #ffc107;
  color: #212529;
}
```

#### Card Components

```html
<!-- HTML -->
<div class="card">
  <div class="card-header">
    <h3 class="card-title">หัวข้อการ์ด</h3>
  </div>
  <div class="card-body">
    <p class="card-text">เนื้อหาของการ์ด</p>
    <a href="#" class="card-link">ลิงก์</a>
  </div>
  <div class="card-footer">
    <small class="text-muted">ข้อมูลเพิ่มเติม</small>
  </div>
</div>
```

```css
/* CSS */
.card {
  background-color: white;
  border: 1px solid #dee2e6;
  border-radius: 0.5rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  margin-bottom: 1rem;
}

.card-header {
  background-color: #f8f9fa;
  border-bottom: 1px solid #dee2e6;
  padding: 1rem;
}

.card-title {
  margin: 0;
  font-size: 1.25rem;
  font-weight: 500;
  color: #495057;
}

.card-body {
  padding: 1rem;
}

.card-text {
  margin-bottom: 1rem;
  line-height: 1.6;
  color: #6c757d;
}

.card-link {
  color: #007bff;
  text-decoration: none;
}

.card-link:hover {
  text-decoration: underline;
}

.card-footer {
  background-color: #f8f9fa;
  border-top: 1px solid #dee2e6;
  padding: 0.75rem 1rem;
}

.text-muted {
  color: #6c757d;
}
```

#### Layout Classes

```html
<!-- HTML -->
<div class="container">
  <div class="row">
    <div class="col">คอลัมน์ 1</div>
    <div class="col">คอลัมน์ 2</div>
    <div class="col">คอลัมน์ 3</div>
  </div>
</div>

<section class="hero">
  <h1 class="hero-title">หัวข้อใหญ่</h1>
  <p class="hero-subtitle">คำบรรยาย</p>
</section>
```

```css
/* CSS */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.row {
  display: flex;
  flex-wrap: wrap;
  margin: 0 -0.5rem;
}

.col {
  flex: 1;
  padding: 0 0.5rem;
  min-width: 0;
}

.hero {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  text-align: center;
  padding: 4rem 2rem;
}

.hero-title {
  font-size: 3rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

.hero-subtitle {
  font-size: 1.25rem;
  opacity: 0.9;
  max-width: 600px;
  margin: 0 auto;
}
```

### หลักการตั้งชื่อ Class

#### BEM Methodology

```css
/* Block Element Modifier */

/* Block */
.menu {
}

/* Element */
.menu__item {
}
.menu__link {
}

/* Modifier */
.menu--horizontal {
}
.menu__item--active {
}
```

```html
<!-- HTML -->
<nav class="menu menu--horizontal">
  <ul class="menu__list">
    <li class="menu__item menu__item--active">
      <a href="#" class="menu__link">หน้าแรก</a>
    </li>
    <li class="menu__item">
      <a href="#" class="menu__link">เกี่ยวกับ</a>
    </li>
  </ul>
</nav>
```

#### Utility Classes

```css
/* Typography */
.text-center {
  text-align: center;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}

.font-bold {
  font-weight: bold;
}
.font-normal {
  font-weight: normal;
}

.text-sm {
  font-size: 0.875rem;
}
.text-lg {
  font-size: 1.125rem;
}
.text-xl {
  font-size: 1.25rem;
}

/* Spacing */
.m-0 {
  margin: 0;
}
.m-1 {
  margin: 0.25rem;
}
.m-2 {
  margin: 0.5rem;
}
.m-3 {
  margin: 1rem;
}

.p-0 {
  padding: 0;
}
.p-1 {
  padding: 0.25rem;
}
.p-2 {
  padding: 0.5rem;
}
.p-3 {
  padding: 1rem;
}

/* Colors */
.text-primary {
  color: #007bff;
}
.text-secondary {
  color: #6c757d;
}
.text-success {
  color: #28a745;
}
.text-danger {
  color: #dc3545;
}

.bg-primary {
  background-color: #007bff;
}
.bg-light {
  background-color: #f8f9fa;
}
.bg-dark {
  background-color: #343a40;
}
```

## 3. ID Selector (ตัวเลือกไอดี)

### ความหมาย

ID Selector เลือก element ที่มี id attribute ตรงกัน โดยใช้เครื่องหมาย `#` นำหน้า

### รูปแบบ

```css
#idname {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### Page Layout

```html
<!-- HTML -->
<!DOCTYPE html>
<html>
  <head>
    <title>Layout Example</title>
  </head>
  <body>
    <header id="main-header">
      <nav id="main-navigation">
        <!-- เมนูหลัก -->
      </nav>
    </header>

    <main id="main-content">
      <aside id="sidebar">
        <!-- แถบข้าง -->
      </aside>
      <section id="content-area">
        <!-- เนื้อหาหลัก -->
      </section>
    </main>

    <footer id="main-footer">
      <!-- ส่วนท้าย -->
    </footer>
  </body>
</html>
```

```css
/* CSS */
#main-header {
  background-color: #2c3e50;
  color: white;
  padding: 1rem 0;
  position: sticky;
  top: 0;
  z-index: 1000;
}

#main-navigation {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

#main-content {
  max-width: 1200px;
  margin: 2rem auto;
  padding: 0 1rem;
  display: grid;
  grid-template-columns: 250px 1fr;
  gap: 2rem;
}

#sidebar {
  background-color: #f8f9fa;
  padding: 1.5rem;
  border-radius: 0.5rem;
  height: fit-content;
}

#content-area {
  background-color: white;
  padding: 2rem;
  border-radius: 0.5rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

#main-footer {
  background-color: #343a40;
  color: white;
  text-align: center;
  padding: 2rem;
  margin-top: 3rem;
}
```

#### Unique Components

```html
<!-- HTML -->
<div id="logo">
  <img src="logo.png" alt="Company Logo" />
</div>

<form id="contact-form">
  <div id="form-header">
    <h2>ติดต่อเรา</h2>
  </div>

  <div id="form-body">
    <input type="text" id="name" placeholder="ชื่อ" />
    <input type="email" id="email" placeholder="อีเมล" />
    <textarea id="message" placeholder="ข้อความ"></textarea>
  </div>

  <div id="form-footer">
    <button type="submit" id="submit-btn">ส่ง</button>
  </div>
</form>

<div id="modal-overlay">
  <div id="modal-content">
    <span id="modal-close">&times;</span>
    <h3 id="modal-title">หัวข้อ Modal</h3>
    <p id="modal-text">เนื้อหา Modal</p>
  </div>
</div>
```

```css
/* CSS */
#logo {
  display: flex;
  align-items: center;
  height: 60px;
}

#logo img {
  height: 100%;
  width: auto;
}

#contact-form {
  max-width: 500px;
  margin: 2rem auto;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}

#form-header {
  background: #007bff;
  color: white;
  padding: 1.5rem;
  text-align: center;
}

#form-header h2 {
  margin: 0;
  font-weight: 500;
}

#form-body {
  padding: 2rem;
}

#form-body input,
#form-body textarea {
  width: 100%;
  padding: 0.75rem;
  margin-bottom: 1rem;
  border: 1px solid #ddd;
  border-radius: 0.25rem;
  font-size: 1rem;
}

#form-body textarea {
  height: 120px;
  resize: vertical;
}

#form-footer {
  padding: 0 2rem 2rem;
}

#submit-btn {
  width: 100%;
  background: #28a745;
  color: white;
  border: none;
  padding: 0.75rem;
  border-radius: 0.25rem;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
}

#submit-btn:hover {
  background: #218838;
}

#modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: none;
  justify-content: center;
  align-items: center;
  z-index: 9999;
}

#modal-content {
  background: white;
  padding: 2rem;
  border-radius: 0.5rem;
  max-width: 500px;
  width: 90%;
  position: relative;
}

#modal-close {
  position: absolute;
  top: 1rem;
  right: 1rem;
  font-size: 1.5rem;
  cursor: pointer;
  color: #aaa;
}

#modal-close:hover {
  color: #000;
}

#modal-title {
  margin: 0 0 1rem 0;
  color: #333;
}

#modal-text {
  margin: 0;
  line-height: 1.6;
  color: #666;
}
```

### เมื่อไหร่ควรใช้ ID

#### ✅ ใช้ ID เมื่อ:

- Element มีเพียงตัวเดียวในหน้า
- ต้องการ JavaScript targeting
- ใช้เป็น anchor links
- Layout components หลัก

#### ❌ ไม่ควรใช้ ID เมื่อ:

- Element อาจมีหลายตัว
- ต้องการ reusable styles
- สร้าง component library

## 4. Universal Selector (ตัวเลือกสากล)

### ความหมาย

Universal Selector เลือกทุก elements ในหน้าเว็บ โดยใช้เครื่องหมาย `*`

### รูปแบบ

```css
* {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### CSS Reset

```css
/* Basic CSS Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* หรือ */
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

#### Typography Reset

```css
* {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```

#### Debug Styles

```css
/* ใช้เพื่อ debug layout */
* {
  border: 1px solid red !important;
}

/* หรือ */
* {
  background-color: rgba(255, 0, 0, 0.1) !important;
}
```

#### Performance Optimization

```css
/* เพิ่มประสิทธิภาพ animations */
*,
*::before,
*::after {
  animation-duration: 0.01ms !important;
  animation-iteration-count: 1 !important;
  transition-duration: 0.01ms !important;
  scroll-behavior: auto !important;
}
```

### ข้อควรระวังในการใช้ Universal Selector

#### ⚠️ ผลกระทบต่อ Performance

```css
/* ❌ หลีกเลี่ยง: การใช้ที่ส่งผลต่อ performance */
* {
  color: red;
  font-size: 16px;
  background: white;
}

/* ✅ ดีกว่า: ใช้เฉพาะที่จำเป็น */
body {
  color: red;
  font-size: 16px;
  background: white;
}
```

#### ⚠️ Specificity Issues

```css
/* Universal selector มี specificity = 0 */
* {
  color: red;
} /* (0,0,0,0) */
p {
  color: blue;
} /* (0,0,0,1) - ชนะ */
.text {
  color: green;
} /* (0,0,1,0) - ชนะ */
```

## 5. Group Selector (ตัวเลือกกลุ่ม)

### ความหมาย

Group Selector ใช้เลือกหลาย selectors พร้อมกัน โดยใช้เครื่องหมาย `,` คั่น

### รูปแบบ

```css
selector1,
selector2,
selector3 {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### Heading Styles

```css
/* แทนที่จะเขียน */
h1 {
  font-family: 'Georgia', serif;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 1rem;
}

h2 {
  font-family: 'Georgia', serif;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 1rem;
}

h3 {
  font-family: 'Georgia', serif;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 1rem;
}

/* ✅ เขียนแบบ group selector */
h1,
h2,
h3 {
  font-family: 'Georgia', serif;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 1rem;
}

/* แล้วกำหนดขนาดแยกต่างหาก */
h1 {
  font-size: 2.5rem;
}
h2 {
  font-size: 2rem;
}
h3 {
  font-size: 1.5rem;
}
```

#### Form Elements

```css
/* Form inputs */
input,
textarea,
select {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #ddd;
  border-radius: 0.25rem;
  font-size: 1rem;
  font-family: inherit;
  transition: border-color 0.3s;
}

input:focus,
textarea:focus,
select:focus {
  outline: none;
  border-color: #007bff;
  box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.1);
}

/* Button styles */
button,
.btn,
input[type='submit'],
input[type='button'] {
  display: inline-block;
  padding: 0.75rem 1.5rem;
  background: #007bff;
  color: white;
  border: none;
  border-radius: 0.25rem;
  cursor: pointer;
  text-decoration: none;
  transition: background-color 0.3s;
}

button:hover,
.btn:hover,
input[type='submit']:hover,
input[type='button']:hover {
  background: #0056b3;
}
```

#### Layout Reset

```css
/* Reset margins และ paddings */
body,
h1,
h2,
h3,
h4,
h5,
h6,
p,
ul,
ol,
li,
figure,
blockquote {
  margin: 0;
  padding: 0;
}

/* List styles */
ul,
ol {
  list-style: none;
}

/* Link styles */
a,
a:visited,
a:hover,
a:active {
  text-decoration: none;
  color: inherit;
}
```

#### Media Elements

```css
/* Responsive images และ media */
img,
video,
audio,
iframe,
object,
embed {
  max-width: 100%;
  height: auto;
}

/* Table elements */
table,
th,
td {
  border-collapse: collapse;
  border: none;
}

th,
td {
  padding: 0.75rem;
  text-align: left;
}
```

### Best Practices สำหรับ Group Selectors

#### 1. จัดเรียงอย่างมีระบบ

```css
/* ✅ ดี: จัดเรียงตาม specificity */
h1,
h2,
h3,
.title,
#main-heading {
  font-family: serif;
}

/* ✅ ดี: จัดเรียงตาม function */
.btn-primary,
.btn-secondary,
.btn-success {
  padding: 0.75rem 1.5rem;
  border-radius: 0.25rem;
}
```

#### 2. ใช้ Comments อธิบาย

```css
/* Typography: Headings */
h1,
h2,
h3,
h4,
h5,
h6 {
  font-weight: 600;
  line-height: 1.2;
}

/* Form Controls */
input[type='text'],
input[type='email'],
input[type='password'],
textarea {
  border: 1px solid #ccc;
}

/* Interactive Elements */
button,
a,
[role='button'] {
  cursor: pointer;
}
```

#### 3. หลีกเลี่ยงการรวมที่ไม่เกี่ยวข้อง

```css
/* ❌ ไม่ดี: รวม selectors ที่ไม่เกี่ยวข้อง */
h1,
.btn,
#sidebar,
input {
  margin-bottom: 1rem;
}

/* ✅ ดี: แยกตาม context */
h1,
h2,
h3 {
  margin-bottom: 1rem;
}

.form-group {
  margin-bottom: 1rem;
}
```

## การเปรียบเทียบ Selectors

### Specificity Comparison

| Selector Type  | Specificity | Example    | Use Case            |
| -------------- | ----------- | ---------- | ------------------- |
| Universal (\*) | (0,0,0,0)   | `*`        | Reset styles        |
| Element        | (0,0,0,1)   | `div`      | Base styling        |
| Class          | (0,0,1,0)   | `.btn`     | Reusable components |
| ID             | (0,1,0,0)   | `#header`  | Unique elements     |
| Inline         | (1,0,0,0)   | `style=""` | Override (avoid)    |

### Performance Comparison

```css
/* เร็วที่สุด: ID Selector */
#navigation {
}

/* เร็ว: Class Selector */
.menu {
}

/* ปานกลาง: Element Selector */
nav {
}

/* ช้าที่สุด: Universal Selector */
* {
}
```

### Use Case Guidelines

#### Element Selectors

```css
/* ✅ ใช้สำหรับ: Base styles */
body {
  font-family: sans-serif;
}
h1,
h2,
h3 {
  color: #333;
}
p {
  line-height: 1.6;
}
a {
  color: blue;
}
```

#### Class Selectors

```css
/* ✅ ใช้สำหรับ: Components และ utilities */
.btn {
  padding: 0.5rem 1rem;
}
.card {
  border: 1px solid #ccc;
}
.text-center {
  text-align: center;
}
.mb-3 {
  margin-bottom: 1rem;
}
```

#### ID Selectors

```css
/* ✅ ใช้สำหรับ: Layout และ unique elements */
#header {
  position: sticky;
}
#main-content {
  max-width: 1200px;
}
#modal {
  position: fixed;
}
```

#### Universal Selector

```css
/* ✅ ใช้สำหรับ: Reset และ global properties */
* {
  box-sizing: border-box;
}
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

#### Group Selectors

```css
/* ✅ ใช้สำหรับ: Shared properties */
h1,
h2,
h3,
h4,
h5,
h6 {
  font-weight: 600;
}
input,
textarea,
select {
  border: 1px solid #ccc;
}
.btn-primary,
.btn-secondary {
  padding: 0.75rem 1.5rem;
}
```

## สรุป

### Basic Selectors สำคัญ 5 ประเภท:

1. **Element Selector** (`tagname`)

   - เลือกตาม HTML tag
   - ใช้สำหรับ base styling
   - Specificity ต่ำ

2. **Class Selector** (`.classname`)

   - เลือกตาม class attribute
   - ใช้สำหรับ components และ utilities
   - Reusable และยืดหยุ่น

3. **ID Selector** (`#idname`)

   - เลือกตาม id attribute
   - ใช้สำหรับ unique elements
   - Specificity สูง

4. **Universal Selector** (`*`)

   - เลือกทุก elements
   - ใช้สำหรับ reset styles
   - ระวัง performance

5. **Group Selector** (`selector1, selector2`)
   - เลือกหลาย selectors พร้อมกัน
   - ลดการเขียน code ซ้ำ
   - จัดกลุ่มอย่างมีเหตุผล

การเข้าใจและใช้ basic selectors อย่างถูกต้องเป็นพื้นฐานสำคัญสำหรับการเขียน CSS ที่มีประสิทธิภาพและง่ายต่อการบำรุงรักษา!
