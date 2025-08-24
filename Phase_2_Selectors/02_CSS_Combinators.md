# CSS Combinators: descendant ( ), child (>), adjacent (+), general sibling (~)

## ภาพรวม CSS Combinators

CSS Combinators เป็นสัญลักษณ์ที่ใช้เชื่อมต่อ selectors เข้าด้วยกัน เพื่อเลือก elements ตามความสัมพันธ์ในโครงสร้าง HTML Tree โดยแต่ละ combinator จะมีวิธีการเลือกที่แตกต่างกัน

### ประเภท Combinators ทั้ง 4 แบบ:

1. **Descendant Combinator** (` `) - ลูกหลาน
2. **Child Combinator** (`>`) - ลูกโดยตรง
3. **Adjacent Sibling Combinator** (`+`) - พี่น้องติดกัน
4. **General Sibling Combinator** (`~`) - พี่น้องทั่วไป

## 1. Descendant Combinator (ลูกหลาน)

### ความหมาย

Descendant Combinator ใช้เว้นวรรค (space) เพื่อเลือก elements ที่เป็นลูกหลานของ element อื่น ไม่ว่าจะลึกกี่ระดับ

### รูปแบบ

```css
ancestor descendant {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### โครงสร้าง HTML

```html
<div class="container">
  <p>ย่อหน้าระดับ 1</p>
  <div class="section">
    <p>ย่อหน้าระดับ 2</p>
    <div class="subsection">
      <p>ย่อหน้าระดับ 3</p>
      <span>
        <p>ย่อหน้าระดับ 4</p>
      </span>
    </div>
  </div>
  <article>
    <p>ย่อหน้าในบทความ</p>
  </article>
</div>

<p>ย่อหน้านอก container</p>
```

#### CSS ที่ใช้ Descendant Combinator

```css
/* เลือก p ทั้งหมดที่อยู่ใน .container (ทุกระดับ) */
.container p {
  color: blue;
  font-size: 16px;
  line-height: 1.6;
}

/* ผลลัพธ์: p ทั้ง 4 ตัวใน .container จะเป็นสีน้ำเงิน */
/* p นอก .container จะไม่ได้รับผลกระทบ */
```

#### ตัวอย่างการใช้งานจริง

##### Navigation Menu

```html
<nav class="main-navigation">
  <ul>
    <li><a href="#home">หน้าแรก</a></li>
    <li>
      <a href="#products">สินค้า</a>
      <ul class="submenu">
        <li><a href="#laptops">แล็ปท็อป</a></li>
        <li><a href="#phones">โทรศัพท์</a></li>
      </ul>
    </li>
    <li><a href="#contact">ติดต่อ</a></li>
  </ul>
</nav>
```

```css
/* เลือก links ทั้งหมดใน navigation */
.main-navigation a {
  text-decoration: none;
  color: #333;
  padding: 0.5rem 1rem;
  display: block;
  transition: background-color 0.3s;
}

.main-navigation a:hover {
  background-color: #f0f0f0;
}

/* เลือก ul ทั้งหมดใน navigation */
.main-navigation ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

/* เลือก li ทั้งหมดใน navigation */
.main-navigation li {
  position: relative;
}

/* เลือก submenu ที่อยู่ใน navigation */
.main-navigation .submenu {
  position: absolute;
  top: 100%;
  left: 0;
  background: white;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  display: none;
}

.main-navigation li:hover .submenu {
  display: block;
}
```

##### Article Styling

```html
<article class="blog-post">
  <header>
    <h1>หัวข้อบทความ</h1>
    <p class="meta">โดย: ผู้เขียน | วันที่: 1 มกราคม 2024</p>
  </header>

  <div class="content">
    <p>ย่อหน้าแรก</p>
    <blockquote>
      <p>ข้อความที่อ้างอิง</p>
    </blockquote>
    <p>ย่อหน้าที่สอง</p>

    <div class="highlight-box">
      <h3>หัวข้อย่อย</h3>
      <p>เนื้อหาในกล่องเน้น</p>
    </div>
  </div>
</article>
```

```css
/* เลือก p ทั้งหมดในบทความ */
.blog-post p {
  line-height: 1.8;
  margin-bottom: 1rem;
  color: #444;
}

/* เลือก headings ทั้งหมดในบทความ */
.blog-post h1,
.blog-post h2,
.blog-post h3 {
  color: #2c3e50;
  font-weight: 600;
}

/* เลือก p ในส่วน content */
.blog-post .content p {
  font-size: 1.1rem;
}

/* เลือก p ใน blockquote */
.blog-post blockquote p {
  font-style: italic;
  color: #666;
  border-left: 4px solid #3498db;
  padding-left: 1rem;
}
```

## 2. Child Combinator (ลูกโดยตรง)

### ความหมาย

Child Combinator ใช้สัญลักษณ์ `>` เพื่อเลือกเฉพาะ elements ที่เป็นลูกโดยตรง (direct children) เท่านั้น

### รูปแบบ

```css
parent > child {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### เปรียบเทียบ Descendant vs Child

```html
<div class="container">
  <p>ลูกโดยตรงของ container</p>
  <div class="wrapper">
    <p>ลูกของ wrapper (ลูกหลานของ container)</p>
    <div class="inner">
      <p>ลูกของ inner (ลูกหลานของ container)</p>
    </div>
  </div>
  <p>ลูกโดยตรงของ container อีกตัว</p>
</div>
```

```css
/* Descendant: เลือก p ทั้งหมดใน .container */
.container p {
  color: blue;
}
/* ผลลัพธ์: p ทั้ง 3 ตัวจะเป็นสีน้ำเงิน */

/* Child: เลือกเฉพาะ p ที่เป็นลูกโดยตรงของ .container */
.container > p {
  font-weight: bold;
}
/* ผลลัพธ์: เฉพาะ p 2 ตัวแรกและสุดท้ายจะเป็นตัวหนา */
```

#### การใช้งานจริง

##### Card Component

```html
<div class="card">
  <div class="card-header">
    <h3>หัวข้อการ์ด</h3>
    <div class="card-actions">
      <button>แก้ไข</button>
      <button>ลบ</button>
    </div>
  </div>

  <div class="card-body">
    <p>เนื้อหาการ์ด</p>
    <div class="card-section">
      <h4>หัวข้อย่อย</h4>
      <p>เนื้อหาในส่วนย่อย</p>
    </div>
  </div>

  <div class="card-footer">
    <button>บันทึก</button>
    <button>ยกเลิก</button>
  </div>
</div>
```

```css
/* เลือกเฉพาะ sections หลักของการ์ด */
.card > div {
  padding: 1rem;
}

/* เลือกเฉพาะ buttons ที่อยู่ใน card-actions โดยตรง */
.card-actions > button {
  margin-left: 0.5rem;
  padding: 0.25rem 0.75rem;
  border: 1px solid #ccc;
  background: white;
  border-radius: 4px;
  cursor: pointer;
}

.card-actions > button:first-child {
  margin-left: 0;
}

/* เลือกเฉพาะ buttons ที่อยู่ใน card-footer โดยตรง */
.card-footer > button {
  margin-right: 0.5rem;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.card-footer > button:last-child {
  margin-right: 0;
}
```

##### Grid Layout

```html
<div class="grid">
  <div class="grid-item">Item 1</div>
  <div class="grid-item">Item 2</div>
  <div class="grid-item">
    Item 3
    <div class="nested">Nested Content</div>
  </div>
  <div class="grid-item">Item 4</div>
</div>
```

```css
/* เลือกเฉพาะ direct children ของ grid */
.grid > .grid-item {
  background: #f0f0f0;
  padding: 1rem;
  border: 1px solid #ddd;
  margin: 0.5rem;
}

/* .nested จะไม่ได้รับ styles จาก .grid > .grid-item */
.grid .nested {
  background: #e0e0e0;
  padding: 0.5rem;
  margin-top: 0.5rem;
}
```

## 3. Adjacent Sibling Combinator (พี่น้องติดกัน)

### ความหมาย

Adjacent Sibling Combinator ใช้สัญลักษณ์ `+` เพื่อเลือก element ที่เป็นพี่น้อง (sibling) และอยู่ติดกันโดยตรง

### รูปแบบ

```css
element1 + element2 {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### โครงสร้าง HTML

```html
<div class="content">
  <h2>หัวข้อ 1</h2>
  <p>ย่อหน้าที่ 1 (ติดกับ h2)</p>
  <p>ย่อหน้าที่ 2</p>

  <h2>หัวข้อ 2</h2>
  <p>ย่อหน้าที่ 3 (ติดกับ h2)</p>
  <ul>
    <li>รายการ 1</li>
    <li>รายการ 2</li>
  </ul>
  <p>ย่อหน้าที่ 4 (ติดกับ ul)</p>

  <div class="note">หมายเหตุ</div>
  <p>ย่อหน้าที่ 5 (ติดกับ .note)</p>
</div>
```

#### CSS ที่ใช้ Adjacent Sibling

```css
/* เลือก p ที่ติดกับ h2 โดยตรง */
h2 + p {
  font-size: 1.2rem;
  font-weight: 600;
  color: #2c3e50;
  margin-top: 0.5rem;
}

/* เลือก p ที่ติดกับ ul โดยตรง */
ul + p {
  margin-top: 1.5rem;
  padding-top: 1rem;
  border-top: 1px solid #eee;
}

/* เลือก p ที่ติดกับ .note โดยตรง */
.note + p {
  background: #fff3cd;
  padding: 1rem;
  border: 1px solid #ffeaa7;
  border-radius: 4px;
}
```

#### การใช้งานจริง

##### Form Layout

```html
<form class="registration-form">
  <label for="name">ชื่อ:</label>
  <input type="text" id="name" name="name" />
  <span class="error">กรุณาใส่ชื่อ</span>

  <label for="email">อีเมล:</label>
  <input type="email" id="email" name="email" />
  <span class="help">ใส่อีเมลที่ถูกต้อง</span>

  <label for="password">รหัสผ่าน:</label>
  <input type="password" id="password" name="password" />

  <button type="submit">สมัครสมาชิก</button>
</form>
```

```css
/* Label styles */
.registration-form label {
  display: block;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: #333;
}

/* Input styles */
.registration-form input {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
}

/* เลือก span ที่ติดกับ input โดยตรง */
.registration-form input + span {
  display: block;
  font-size: 0.875rem;
  margin-top: 0.25rem;
  margin-bottom: 1rem;
}

/* Error message (class .error) */
.registration-form input + span.error {
  color: #dc3545;
}

/* Help message (class .help) */
.registration-form input + span.help {
  color: #6c757d;
}

/* Button ที่ติดกับ input โดยตรง */
.registration-form input + button {
  margin-top: 1rem;
  width: 100%;
  background: #007bff;
  color: white;
  border: none;
  padding: 0.75rem;
  border-radius: 4px;
  cursor: pointer;
}
```

##### Article Typography

```html
<article>
  <h1>หัวข้อหลัก</h1>
  <p class="lead">ย่อหน้าเกริ่นนำ</p>
  <p>ย่อหน้าปกติ</p>

  <h2>หัวข้อรอง</h2>
  <p>ย่อหน้าหลังหัวข้อรอง</p>
  <p>ย่อหน้าต่อไป</p>

  <blockquote>ข้อความอ้างอิง</blockquote>
  <p>ย่อหน้าหลัง blockquote</p>
</article>
```

```css
/* ย่อหน้าแรกหลัง h1 */
h1 + p {
  font-size: 1.25rem;
  font-weight: 300;
  color: #666;
  margin-bottom: 2rem;
}

/* ย่อหน้าแรกหลัง h2 */
h2 + p {
  margin-top: 0.5rem;
  font-weight: 500;
}

/* ย่อหน้าหลัง blockquote */
blockquote + p {
  margin-top: 1.5rem;
  font-style: italic;
  color: #555;
}
```

## 4. General Sibling Combinator (พี่น้องทั่วไป)

### ความหมาย

General Sibling Combinator ใช้สัญลักษณ์ `~` เพื่อเลือก elements ที่เป็นพี่น้องกัน แต่ไม่จำเป็นต้องติดกัน

### รูปแบบ

```css
element1 ~ element2 {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### เปรียบเทียบ Adjacent vs General Sibling

```html
<div class="container">
  <h2>หัวข้อ</h2>
  <div class="spacer"></div>
  <p>ย่อหน้า 1</p>
  <span>ข้อความ</span>
  <p>ย่อหน้า 2</p>
  <div class="box"></div>
  <p>ย่อหน้า 3</p>
</div>
```

```css
/* Adjacent: เลือกเฉพาะ element ที่ติดกับ h2 โดยตรง */
h2 + p {
  color: red;
}
/* ผลลัพธ์: ไม่มี p ใดเป็นสีแดง (เพราะมี .spacer คั่น) */

/* General Sibling: เลือก p ทั้งหมดที่เป็นพี่น้องกับ h2 */
h2 ~ p {
  color: blue;
}
/* ผลลัพธ์: p ทั้ง 3 ตัวจะเป็นสีน้ำเงิน */
```

#### การใช้งานจริง

##### Tab System

```html
<div class="tabs">
  <input type="radio" id="tab1" name="tabs" checked />
  <label for="tab1">แท็บ 1</label>

  <input type="radio" id="tab2" name="tabs" />
  <label for="tab2">แท็บ 2</label>

  <input type="radio" id="tab3" name="tabs" />
  <label for="tab3">แท็บ 3</label>

  <div class="tab-content" data-tab="1">
    <h3>เนื้อหาแท็บ 1</h3>
    <p>เนื้อหาของแท็บแรก</p>
  </div>

  <div class="tab-content" data-tab="2">
    <h3>เนื้อหาแท็บ 2</h3>
    <p>เนื้อหาของแท็บที่สอง</p>
  </div>

  <div class="tab-content" data-tab="3">
    <h3>เนื้อหาแท็บ 3</h3>
    <p>เนื้อหาของแท็บที่สาม</p>
  </div>
</div>
```

```css
/* ซ่อน radio buttons */
.tabs input[type='radio'] {
  display: none;
}

/* Tab labels */
.tabs label {
  display: inline-block;
  padding: 0.75rem 1.5rem;
  background: #f8f9fa;
  border: 1px solid #dee2e6;
  cursor: pointer;
  margin-right: -1px;
}

/* ซ่อน tab content ทั้งหมด */
.tabs .tab-content {
  display: none;
  padding: 2rem;
  border: 1px solid #dee2e6;
  border-top: none;
}

/* แสดง tab content เมื่อ radio button ถูกเลือก */
.tabs input:checked ~ .tab-content[data-tab='1'] {
  display: block;
}

#tab1:checked ~ .tab-content[data-tab='1'],
#tab2:checked ~ .tab-content[data-tab='2'],
#tab3:checked ~ .tab-content[data-tab='3'] {
  display: block;
}

/* Active tab label */
#tab1:checked ~ label[for='tab1'],
#tab2:checked ~ label[for='tab2'],
#tab3:checked ~ label[for='tab3'] {
  background: white;
  border-bottom: 1px solid white;
}
```

##### Accordion System

```html
<div class="accordion">
  <input type="checkbox" id="section1" />
  <label for="section1">หัวข้อส่วนที่ 1</label>
  <div class="accordion-content">
    <p>เนื้อหาส่วนที่ 1</p>
  </div>

  <input type="checkbox" id="section2" />
  <label for="section2">หัวข้อส่วนที่ 2</label>
  <div class="accordion-content">
    <p>เนื้อหาส่วนที่ 2</p>
  </div>

  <input type="checkbox" id="section3" />
  <label for="section3">หัวข้อส่วนที่ 3</label>
  <div class="accordion-content">
    <p>เนื้อหาส่วนที่ 3</p>
  </div>
</div>
```

```css
/* ซ่อน checkboxes */
.accordion input[type='checkbox'] {
  display: none;
}

/* Accordion headers */
.accordion label {
  display: block;
  padding: 1rem;
  background: #f8f9fa;
  border: 1px solid #dee2e6;
  border-bottom: none;
  cursor: pointer;
  font-weight: 600;
  position: relative;
}

.accordion label:last-of-type {
  border-bottom: 1px solid #dee2e6;
}

/* ซ่อน content ทั้งหมด */
.accordion .accordion-content {
  max-height: 0;
  overflow: hidden;
  background: white;
  border: 1px solid #dee2e6;
  border-top: none;
  border-bottom: none;
  transition: max-height 0.3s ease;
}

/* แสดง content เมื่อ checkbox ถูกเลือก */
.accordion input:checked ~ .accordion-content {
  max-height: 200px;
  padding: 1rem;
  border-bottom: 1px solid #dee2e6;
}

/* เปลี่ยน label เมื่อ active */
.accordion input:checked ~ label {
  background: #e9ecef;
}
```

## การเปรียบเทียบ Combinators ทั้ง 4 แบบ

### ตารางเปรียบเทียบ

| Combinator           | สัญลักษณ์   | ความสัมพันธ์       | ตัวอย่าง  | การเลือก               |
| -------------------- | ----------- | ------------------ | --------- | ---------------------- |
| **Descendant**       | ` ` (space) | ลูกหลาน (ทุกระดับ) | `div p`   | p ทั้งหมดใน div        |
| **Child**            | `>`         | ลูกโดยตรง          | `div > p` | p ที่เป็นลูกตรงของ div |
| **Adjacent Sibling** | `+`         | พี่น้องติดกัน      | `h2 + p`  | p ที่ติดหลัง h2        |
| **General Sibling**  | `~`         | พี่น้องทั่วไป      | `h2 ~ p`  | p ทั้งหมดหลัง h2       |

### ตัวอย่างครอบคลุม

```html
<div class="example">
  <h2>หัวข้อ</h2>
  <p>P1: ติดกับ h2</p>
  <div class="wrapper">
    <p>P2: ลูกของ wrapper</p>
    <span>
      <p>P3: ลูกหลานของ wrapper</p>
    </span>
  </div>
  <p>P4: พี่น้องกับ wrapper</p>
  <section>
    <p>P5: ลูกของ section</p>
  </section>
  <p>P6: พี่น้องกับ section</p>
</div>
```

```css
/* Descendant: เลือก p ทั้งหมดใน .example */
.example p {
  border-left: 3px solid #ccc;
  padding-left: 1rem;
}
/* ผลลัพธ์: P1, P2, P3, P4, P5, P6 ทุกตัว */

/* Child: เลือก p ที่เป็นลูกตรงของ .example */
.example > p {
  background: #f0f0f0;
}
/* ผลลัพธ์: P1, P4, P6 เท่านั้น */

/* Adjacent Sibling: เลือก p ที่ติดหลัง h2 */
h2 + p {
  font-weight: bold;
}
/* ผลลัพธ์: P1 เท่านั้น */

/* General Sibling: เลือก p ทั้งหมดหลัง h2 */
h2 ~ p {
  margin-left: 2rem;
}
/* ผลลัพธ์: P1, P4, P6 เท่านั้น (P2, P3, P5 ไม่ใช่พี่น้อง) */
```

## Use Cases และ Best Practices

### 1. การจัด Typography

```css
/* ย่อหน้าแรกของบทความ */
.article h1 + p {
  font-size: 1.2rem;
  color: #666;
}

/* ย่อหน้าหลัง blockquote */
blockquote + p {
  margin-top: 1.5rem;
}

/* รายการหลังหัวข้อ */
h3 + ul,
h3 + ol {
  margin-top: 0.5rem;
}
```

### 2. Form Styling

```css
/* Label ที่อยู่เหนือ input */
label + input,
label + textarea,
label + select {
  margin-top: 0.25rem;
}

/* Error message หลัง input */
input:invalid + .error-message {
  display: block;
  color: #dc3545;
}

/* Help text หลัง input */
input + .help-text {
  font-size: 0.875rem;
  color: #6c757d;
}
```

### 3. Layout Components

```css
/* Card components */
.card > .card-header {
  border-bottom: 1px solid #dee2e6;
}

.card > .card-footer {
  border-top: 1px solid #dee2e6;
}

/* Grid items */
.grid > .grid-item {
  flex: 1;
  padding: 1rem;
}

/* Navigation items */
.nav > .nav-item {
  display: inline-block;
}
```

### 4. Interactive Elements

```css
/* Tabs */
.tab-button:checked ~ .tab-content {
  display: block;
}

/* Dropdowns */
.dropdown:hover > .dropdown-menu {
  display: block;
}

/* Accordions */
.accordion-trigger:checked ~ .accordion-content {
  max-height: 500px;
}
```

## ข้อควรระวังและข้อผิดพลาดที่พบบ่อย

### 1. ความเข้าใจผิดเรื่อง Specificity

```css
/* ❌ เข้าใจผิด: คิดว่า child combinator มี specificity สูงกว่า */
div p {
  color: red;
} /* (0,0,0,2) */
div > p {
  color: blue;
} /* (0,0,0,2) - เท่ากัน! */

/* ผลลัพธ์: สีน้ำเงิน (rule หลังชนะ) */
```

### 2. การใช้ Adjacent Combinator ผิด

```html
<!-- HTML -->
<div>
  <h2>หัวข้อ</h2>
  <!-- มี whitespace หรือ comment ตรงนี้ -->
  <p>ย่อหน้า</p>
</div>
```

```css
/* ❌ อาจไม่ทำงานเพราะมี whitespace คั่น */
h2 + p {
  color: red;
}

/* ✅ ใช้ descendant หรือตรวจสอบ HTML */
h2 ~ p {
  color: red;
}
```

### 3. Performance Issues

```css
/* ❌ ช้า: descendant ที่ลึกมาก */
.container .wrapper .section .content .text p {
  color: red;
}

/* ✅ เร็วกว่า: ใช้ class */
.text-content {
  color: red;
}
```

## สรุป

### Combinators ทั้ง 4 แบบ:

1. **Descendant (` `)**

   - เลือกลูกหลานทุกระดับ
   - ใช้บ่อยที่สุด
   - ระวัง performance

2. **Child (`>`)**

   - เลือกเฉพาะลูกโดยตรง
   - ควบคุมได้แม่นยำ
   - เหมาะสำหรับ layout

3. **Adjacent Sibling (`+`)**

   - เลือกพี่น้องติดกัน
   - เหมาะสำหรับ typography
   - ใช้กับ form styling

4. **General Sibling (`~`)**
   - เลือกพี่น้องทั้งหมด
   - เหมาะสำหรับ interactive UI
   - ใช้กับ tabs, accordions

### หลักการใช้งาน:

- **เลือก combinator ที่เหมาะสมกับโครงสร้าง**
- **ใช้ child combinator เมื่อต้องการความแม่นยำ**
- **ใช้ sibling combinators สำหรับ UI patterns**
- **ระวัง performance กับ descendant ที่ซับซ้อน**

การเข้าใจ CSS Combinators จะช่วยให้เขียน CSS ที่มีประสิทธิภาพและควบคุม layout ได้อย่างแม่นยำ!
