# CSS Pseudo-elements: ::before, ::after, ::first-line, ::first-letter, ::selection, ::placeholder

## ภาพรวม CSS Pseudo-elements

CSS Pseudo-elements เป็นเครื่องมือที่ทรงพลังในการสร้างและจัดสไตล์ส่วนของ element ที่ไม่มีอยู่จริงใน HTML โดยสามารถเพิ่มเนื้อหา สร้างเอฟเฟกต์ หรือจัดสไตล์ส่วนเฉพาะของข้อความได้

### ความแตกต่างระหว่าง Pseudo-classes และ Pseudo-elements

```css
/* Pseudo-class - เลือกตามสถานะ */
a:hover {
  color: red;
}

/* Pseudo-element - สร้างส่วนใหม่ของ element */
p::first-letter {
  font-size: 2em;
}
```

### รูปแบบการเขียน

```css
/* Syntax เก่า (single colon) - ยังใช้ได้ */
element:before {
  content: '';
}

/* Syntax ใหม่ (double colon) - แนะนำ */
element::before {
  content: '';
}
```

### Pseudo-elements หลัก 6 ตัว

1. **::before** - เพิ่มเนื้อหาก่อน element
2. **::after** - เพิ่มเนื้อหาหลัง element
3. **::first-line** - บรรทัดแรกของ element
4. **::first-letter** - ตัวอักษรแรกของ element
5. **::selection** - ข้อความที่ถูกเลือก
6. **::placeholder** - placeholder text ใน input

## 1. ::before - เพิ่มเนื้อหาก่อน Element

### ความหมาย

`::before` สร้าง pseudo-element ที่เป็น child แรกของ element ที่เลือก มักใช้เพิ่มเนื้อหาตกแต่งหรือไอคอน

### คุณสมบัติพื้นฐาน

```css
element::before {
  content: ''; /* จำเป็นต้องมี */
  display: inline; /* default */
  /* properties อื่นๆ */
}
```

### ตัวอย่างการใช้งาน

#### เพิ่มไอคอนและสัญลักษณ์

```html
<!-- HTML -->
<div class="icon-examples">
  <h2 class="with-star">หัวข้อสำคัญ</h2>
  <p class="with-quote">ข้อความที่ต้องการเน้น</p>
  <a href="#" class="external-link">ลิงก์ภายนอก</a>
  <div class="notification">การแจ้งเตือนใหม่</div>
</div>
```

```css
/* เพิ่มดาวหน้าหัวข้อ */
.with-star::before {
  content: '⭐ ';
  color: #f39c12;
  font-size: 1.2em;
}

/* เพิ่มเครื่องหมายคำพูด */
.with-quote::before {
  content: '' ';
    font-size: 2em;
    color: #3498db;
    line-height: 0;
    vertical-align: -0.2em;
    margin-right: 0.1em;
}

.with-quote::after {
    content: ' '';
  font-size: 2em;
  color: #3498db;
  line-height: 0;
  vertical-align: -0.2em;
  margin-left: 0.1em;
}

/* ไอคอนลิงก์ภายนอก */
.external-link::before {
  content: '🌐 ';
  margin-right: 0.25em;
}

/* จุดแจ้งเตือน */
.notification::before {
  content: '';
  display: inline-block;
  width: 8px;
  height: 8px;
  background: #e74c3c;
  border-radius: 50%;
  margin-right: 0.5em;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}
```

#### สร้างรูปทรงและเอฟเฟกต์

```html
<!-- HTML -->
<div class="shape-examples">
  <div class="triangle-box">กล่องที่มีลูกศรชี้</div>
  <div class="ribbon">ป้ายริบบิ้น</div>
  <div class="corner-ribbon">มุมริบบิ้น</div>
  <button class="btn-with-border">ปุ่มขอบสวย</button>
</div>
```

```css
/* กล่องที่มีลูกศรชี้ */
.triangle-box {
  background: #3498db;
  color: white;
  padding: 1rem;
  border-radius: 4px;
  position: relative;
  margin: 2rem 0;
}

.triangle-box::before {
  content: '';
  position: absolute;
  top: 100%;
  left: 2rem;
  width: 0;
  height: 0;
  border-left: 10px solid transparent;
  border-right: 10px solid transparent;
  border-top: 10px solid #3498db;
}

/* ริบบิ้น */
.ribbon {
  background: #e74c3c;
  color: white;
  padding: 0.5rem 2rem;
  position: relative;
  display: inline-block;
  margin: 2rem;
}

.ribbon::before,
.ribbon::after {
  content: '';
  position: absolute;
  top: 0;
  width: 0;
  height: 0;
  border-top: 1.5rem solid #c0392b;
  border-bottom: 1.5rem solid #c0392b;
}

.ribbon::before {
  left: -1rem;
  border-right: 1rem solid #e74c3c;
}

.ribbon::after {
  right: -1rem;
  border-left: 1rem solid #e74c3c;
}

/* มุมริบบิ้น */
.corner-ribbon {
  position: relative;
  background: #ecf0f1;
  padding: 2rem;
  margin: 2rem;
}

.corner-ribbon::before {
  content: 'ใหม่';
  position: absolute;
  top: 0.5rem;
  right: -0.5rem;
  background: #e74c3c;
  color: white;
  padding: 0.25rem 1.5rem;
  font-size: 0.8rem;
  transform: rotate(45deg);
  transform-origin: center;
}

/* ปุ่มขอบแอนิเมชัน */
.btn-with-border {
  background: transparent;
  border: 2px solid #3498db;
  color: #3498db;
  padding: 0.75rem 1.5rem;
  position: relative;
  overflow: hidden;
  cursor: pointer;
  transition: color 0.3s;
}

.btn-with-border::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: #3498db;
  transition: left 0.3s ease;
  z-index: -1;
}

.btn-with-border:hover {
  color: white;
}

.btn-with-border:hover::before {
  left: 0;
}
```

#### สร้าง Loading และ Progress Indicators

```html
<!-- HTML -->
<div class="loading-examples">
  <div class="spinner">กำลังโหลด</div>
  <div class="progress-bar" data-progress="75">ความคืบหน้า</div>
  <div class="dots-loading">รอสักครู่</div>
</div>
```

```css
/* Spinner */
.spinner {
  position: relative;
  padding-left: 2rem;
}

.spinner::before {
  content: '';
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 1rem;
  height: 1rem;
  border: 2px solid #bdc3c7;
  border-top: 2px solid #3498db;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% {
    transform: translateY(-50%) rotate(0deg);
  }
  100% {
    transform: translateY(-50%) rotate(360deg);
  }
}

/* Progress Bar */
.progress-bar {
  background: #ecf0f1;
  height: 1.5rem;
  border-radius: 0.75rem;
  position: relative;
  overflow: hidden;
  text-align: center;
  line-height: 1.5rem;
  color: white;
  font-weight: bold;
}

.progress-bar::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: attr(data-progress '%', 0%);
  background: linear-gradient(45deg, #3498db, #2ecc71);
  border-radius: 0.75rem;
  transition: width 0.3s ease;
}

/* ใช้ CSS custom properties สำหรับ progress */
.progress-bar[data-progress='75']::before {
  width: 75%;
}

/* Dots Loading */
.dots-loading::after {
  content: '';
  display: inline-block;
  animation: dots 1.5s infinite;
}

@keyframes dots {
  0%,
  20% {
    content: '';
  }
  40% {
    content: '.';
  }
  60% {
    content: '..';
  }
  80%,
  100% {
    content: '...';
  }
}
```

## 2. ::after - เพิ่มเนื้อหาหลัง Element

### ความหมาย

`::after` สร้าง pseudo-element ที่เป็น child สุดท้ายของ element ที่เลือก มักใช้คู่กับ `::before`

### ตัวอย่างการใช้งาน

#### สร้าง Tooltips

```html
<!-- HTML -->
<div class="tooltip-examples">
  <span class="tooltip" data-tooltip="ข้อมูลเพิ่มเติมเกี่ยวกับเรื่องนี้"
    >วางเมาส์ที่นี่</span
  >
  <button class="btn-tooltip" data-tooltip="คลิกเพื่อบันทึกข้อมูล">
    บันทึก
  </button>
  <a href="#" class="link-tooltip" data-tooltip="ลิงก์นี้จะพาไปหน้าใหม่"
    >ไปหน้าอื่น</a
  >
</div>
```

```css
/* Base tooltip styling */
[data-tooltip] {
  position: relative;
  cursor: help;
}

[data-tooltip]::before,
[data-tooltip]::after {
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  opacity: 0;
  pointer-events: none;
  transition: all 0.3s ease;
}

/* Tooltip content */
[data-tooltip]::before {
  content: attr(data-tooltip);
  background: #2c3e50;
  color: white;
  padding: 0.5rem 0.75rem;
  border-radius: 4px;
  font-size: 0.85rem;
  white-space: nowrap;
  margin-bottom: 0.5rem;
  max-width: 200px;
  white-space: normal;
  text-align: center;
}

/* Tooltip arrow */
[data-tooltip]::after {
  content: '';
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 5px solid #2c3e50;
  margin-bottom: -5px;
}

/* Show tooltip on hover */
[data-tooltip]:hover::before,
[data-tooltip]:hover::after {
  opacity: 1;
  transform: translateX(-50%) translateY(-5px);
}

/* Different tooltip positions */
.tooltip-left::before,
.tooltip-left::after {
  left: 0;
  right: 100%;
  top: 50%;
  bottom: auto;
  transform: translateY(-50%);
}

.tooltip-left:hover::before,
.tooltip-left:hover::after {
  transform: translateY(-50%) translateX(-5px);
}
```

#### สร้าง Badges และ Counters

```html
<!-- HTML -->
<div class="badge-examples">
  <span class="notification-badge" data-count="5">ข้อความ</span>
  <button class="cart-badge" data-items="12">🛒 ตะกร้า</button>
  <div class="status-online">ผู้ใช้ออนไลน์</div>
  <div class="new-item">สินค้าใหม่</div>
</div>
```

```css
/* Notification badge */
.notification-badge {
  position: relative;
  display: inline-block;
  padding: 0.5rem 1rem;
  background: #3498db;
  color: white;
  border-radius: 4px;
}

.notification-badge::after {
  content: attr(data-count);
  position: absolute;
  top: -0.5rem;
  right: -0.5rem;
  background: #e74c3c;
  color: white;
  border-radius: 50%;
  width: 1.5rem;
  height: 1.5rem;
  font-size: 0.75rem;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
}

/* Cart badge */
.cart-badge {
  position: relative;
  background: #2ecc71;
  color: white;
  border: none;
  padding: 0.75rem 1rem;
  border-radius: 4px;
  cursor: pointer;
}

.cart-badge::after {
  content: attr(data-items);
  position: absolute;
  top: -0.25rem;
  right: -0.25rem;
  background: #f39c12;
  color: white;
  border-radius: 0.75rem;
  padding: 0.1rem 0.4rem;
  font-size: 0.7rem;
  min-width: 1.2rem;
  text-align: center;
}

/* Status indicator */
.status-online {
  position: relative;
  padding-left: 1.5rem;
}

.status-online::before {
  content: '';
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 0.75rem;
  height: 0.75rem;
  background: #2ecc71;
  border-radius: 50%;
  animation: pulse-green 2s infinite;
}

@keyframes pulse-green {
  0%,
  100% {
    box-shadow: 0 0 0 0 rgba(46, 204, 113, 0.7);
  }
  50% {
    box-shadow: 0 0 0 10px rgba(46, 204, 113, 0);
  }
}

/* New item label */
.new-item {
  position: relative;
  display: inline-block;
  padding: 1rem;
  background: #ecf0f1;
  border-radius: 4px;
}

.new-item::after {
  content: 'ใหม่!';
  position: absolute;
  top: -0.5rem;
  right: -0.5rem;
  background: #e74c3c;
  color: white;
  padding: 0.25rem 0.5rem;
  border-radius: 3px;
  font-size: 0.7rem;
  font-weight: bold;
  transform: rotate(15deg);
}
```

## 3. ::first-line - บรรทัดแรก

### ความหมาย

`::first-line` เลือกบรรทัดแรกของ block element สำหรับการจัดสไตล์

### ข้อจำกัด

- ใช้ได้เฉพาะ block elements
- Properties ที่ใช้ได้จำกัด: font, color, background, text-decoration, etc.

### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<div class="typography-examples">
  <article class="news-article">
    <p class="lead-paragraph">
      นี่คือย่อหน้าเปิดของบทความข่าว
      ซึ่งมักจะมีความสำคัญและต้องการให้โดดเด่นกว่าเนื้อหาส่วนอื่น
      โดยบรรทัดแรกควรจะดึงดูดความสนใจของผู้อ่าน และทำให้ต้องการอ่านต่อไป
    </p>

    <p class="body-text">
      เนื้อหาในส่วนนี้เป็นเนื้อหาปกติของบทความ
      ซึ่งจะมีการจัดรูปแบบที่แตกต่างจากย่อหน้าเปิด
      เพื่อให้เกิดลำดับชั้นของข้อมูลที่ชัดเจน และง่ายต่อการอ่าน
    </p>
  </article>

  <div class="quote-block">
    <blockquote>
      "การออกแบบที่ดีคือการออกแบบที่ไม่เห็น
      มันทำงานได้อย่างลื่นไหลและไม่ขัดขวางผู้ใช้ในการทำสิ่งที่ต้องการ"
    </blockquote>
  </div>
</div>
```

```css
/* Lead paragraph - บรรทัดแรกใหญ่และโดดเด่น */
.lead-paragraph::first-line {
    font-size: 1.3em;
    font-weight: 700;
    color: #2c3e50;
    letter-spacing: 0.5px;
}

.lead-paragraph {
    font-size: 1.1rem;
    line-height: 1.7;
    color: #34495e;
    margin-bottom: 2rem;
}

/* Body text - บรรทัดแรกมีสไตล์เบาๆ */
.body-text::first-line {
    font-variant: small-caps;
    letter-spacing: 1px;
    color: #3498db;
}

.body-text {
    font-size: 1rem;
    line-height: 1.6;
    color: #555;
    margin-bottom: 1rem;
}

/* Quote block - บรรทัดแรกเป็นตัวเอียงและใหญ่ขึ้น */
.quote-block blockquote::first-line {
    font-size: 1.4em;
    font-style: italic;
    color: #e74c3c;
    font-weight: 300;
}

.quote-block blockquote {
    font-size: 1.2rem;
    line-height: 1.5;
    padding: 2rem;
    border-left: 4px solid #3498db;
    background: #f8f9fa;
    margin: 2rem 0;
    position: relative;
}

/* เพิ่มเครื่องหมายคำพูดใหญ่ */
.quote-block blockquote::before {
    content: """;
    font-size: 4rem;
    color: #bdc3c7;
    position: absolute;
    top: -1rem;
    left: 1rem;
    line-height: 1;
}
```

## 4. ::first-letter - ตัวอักษรแรก

### ความหมาย

`::first-letter` เลือกตัวอักษรแรกของ block element สำหรับการสร้าง drop cap หรือการเน้นตัวอักษรแรก

### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<div class="drop-cap-examples">
  <article class="classic-article">
    <p class="opening-paragraph">
      ครั้งหนึ่งนานมาแล้ว ในดินแดนอันไกลโพ้น
      มีเจ้าหญิงองค์หนึ่งที่อาศัยอยู่ในปราสาทสูงตระหง่าน
      เธอมีความงามที่ไม่มีใครเทียบได้ และมีจิตใจที่ใจดีต่อทุกคน
    </p>
  </article>

  <article class="modern-article">
    <p class="tech-paragraph">
      เทคโนโลยีในยุคปัจจุบันได้เปลี่ยนแปลงวิถีชีวิตของเราอย่างมากมาย
      ตั้งแต่การสื่อสารไปจนถึงการทำงาน ทุกอย่างล้วนเชื่อมโยงกันผ่านระบบดิจิทัล
    </p>
  </article>

  <article class="magazine-style">
    <p class="feature-story">
      ศิลปะการถ่ายภาพในยุคดิจิทัล ได้รับการพัฒนาไปอย่างมากในช่วงทศวรรษที่ผ่านมา
      ทำให้ผู้คนทั่วไปสามารถเข้าถึงเครื่องมือที่มีคุณภาพสูงได้ง่ายขึ้น
    </p>
  </article>
</div>
```

```css
/* Classic drop cap */
.classic-article .opening-paragraph::first-letter {
  float: left;
  font-size: 4em;
  line-height: 0.8;
  padding: 0.1em 0.1em 0 0;
  margin: 0.1em 0.1em 0 0;
  font-family: 'Georgia', serif;
  font-weight: bold;
  color: #8b4513;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.classic-article .opening-paragraph {
  font-family: 'Georgia', serif;
  font-size: 1.1rem;
  line-height: 1.8;
  text-align: justify;
  text-indent: 0;
}

/* Modern tech style */
.modern-article .tech-paragraph::first-letter {
  float: left;
  font-size: 3.5em;
  line-height: 1;
  padding: 0;
  margin: 0.05em 0.15em 0 0;
  font-family: 'Arial', sans-serif;
  font-weight: 900;
  background: linear-gradient(45deg, #3498db, #2ecc71);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  border: 3px solid #3498db;
  border-radius: 8px;
  padding: 0.1em;
}

.modern-article .tech-paragraph {
  font-family: 'Arial', sans-serif;
  font-size: 1rem;
  line-height: 1.6;
  color: #333;
}

/* Magazine style with background */
.magazine-style .feature-story::first-letter {
  float: left;
  font-size: 3em;
  line-height: 1;
  padding: 0.2em;
  margin: 0.1em 0.15em 0 0;
  background: #e74c3c;
  color: white;
  border-radius: 50%;
  text-align: center;
  width: 1.5em;
  height: 1.5em;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.magazine-style .feature-story {
  font-family: 'Helvetica', sans-serif;
  font-size: 1rem;
  line-height: 1.7;
  color: #444;
}

/* Responsive drop caps */
@media (max-width: 768px) {
  .classic-article .opening-paragraph::first-letter,
  .modern-article .tech-paragraph::first-letter,
  .magazine-style .feature-story::first-letter {
    font-size: 2.5em;
    margin: 0.05em 0.1em 0 0;
  }
}
```

## 5. ::selection - ข้อความที่ถูกเลือก

### ความหมาย

`::selection` เลือกส่วนของข้อความที่ผู้ใช้เลือก (highlight) ด้วยเมาส์หรือ keyboard

### Properties ที่รองรับ

- color
- background-color
- text-shadow

### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<div class="selection-examples">
  <div class="default-selection">
    <p>ลองเลือกข้อความในย่อหน้านี้ดู คุณจะเห็นสีที่กำหนดเอง</p>
  </div>

  <div class="brand-selection">
    <h2>หัวข้อของแบรนด์</h2>
    <p>เนื้อหาที่เกี่ยวกับแบรนด์ ลองเลือกข้อความเพื่อดูสีของแบรนด์</p>
  </div>

  <div class="code-selection">
    <pre><code>function hello() {
    console.log("Hello World!");
    return true;
}</code></pre>
  </div>

  <div class="no-select">
    <p>ข้อความในส่วนนี้เลือกไม่ได้</p>
  </div>
</div>
```

```css
/* Global selection styling */
::selection {
  background: #3498db;
  color: white;
  text-shadow: none;
}

/* Firefox support */
::-moz-selection {
  background: #3498db;
  color: white;
  text-shadow: none;
}

/* Default selection area */
.default-selection::selection {
  background: #e74c3c;
  color: white;
}

.default-selection::-moz-selection {
  background: #e74c3c;
  color: white;
}

/* Brand colors selection */
.brand-selection::selection {
  background: linear-gradient(45deg, #667eea, #764ba2);
  color: white;
}

.brand-selection h2::selection {
  background: #f39c12;
  color: #2c3e50;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
}

/* Code block selection */
.code-selection {
  background: #2c3e50;
  color: #ecf0f1;
  padding: 1rem;
  border-radius: 4px;
  font-family: 'Courier New', monospace;
}

.code-selection::selection {
  background: #f39c12;
  color: #2c3e50;
}

.code-selection::-moz-selection {
  background: #f39c12;
  color: #2c3e50;
}

/* Disable text selection */
.no-select {
  user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  background: #ecf0f1;
  padding: 1rem;
  border-radius: 4px;
  cursor: default;
}

/* Multiple selection styles for different elements */
h1::selection {
  background: #e74c3c;
  color: white;
}
h2::selection {
  background: #f39c12;
  color: white;
}
h3::selection {
  background: #2ecc71;
  color: white;
}
a::selection {
  background: #9b59b6;
  color: white;
}
code::selection {
  background: #34495e;
  color: #f39c12;
}
```

## 6. ::placeholder - ข้อความ Placeholder

### ความหมาย

`::placeholder` เลือก placeholder text ใน input และ textarea elements

### Browser Support

```css
/* Modern browsers */
::placeholder {
  color: #999;
}

/* WebKit browsers */
::-webkit-input-placeholder {
  color: #999;
}

/* Firefox 18- */
:-moz-placeholder {
  color: #999;
  opacity: 1;
}

/* Firefox 19+ */
::-moz-placeholder {
  color: #999;
  opacity: 1;
}

/* Internet Explorer 10+ */
:-ms-input-placeholder {
  color: #999;
}
```

### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<div class="form-examples">
  <form class="modern-form">
    <div class="form-group">
      <input type="text" placeholder="ชื่อผู้ใช้งาน" class="username-input" />
    </div>

    <div class="form-group">
      <input type="email" placeholder="อีเมลของคุณ" class="email-input" />
    </div>

    <div class="form-group">
      <input
        type="password"
        placeholder="รหัสผ่าน (อย่างน้อย 8 ตัวอักษร)"
        class="password-input"
      />
    </div>

    <div class="form-group">
      <textarea
        placeholder="เขียนข้อความของคุณที่นี่..."
        class="message-textarea"
      ></textarea>
    </div>

    <div class="form-group">
      <input type="search" placeholder="🔍 ค้นหา..." class="search-input" />
    </div>
  </form>

  <form class="creative-form">
    <input
      type="text"
      placeholder="✨ ชื่อมหัศจรรย์ของคุณ"
      class="magic-input"
    />
    <input type="email" placeholder="📧 อีเมลวิเศษ" class="magic-input" />
    <textarea
      placeholder="💭 แบ่งปันความคิดสร้างสรรค์..."
      class="magic-textarea"
    ></textarea>
  </form>
</div>
```

```css
/* Modern form placeholders */
.modern-form input::placeholder,
.modern-form textarea::placeholder {
  color: #7f8c8d;
  font-style: italic;
  transition: color 0.3s ease;
}

.modern-form input:focus::placeholder,
.modern-form textarea:focus::placeholder {
  color: #bdc3c7;
  transform: translateX(5px);
}

/* Specific input types */
.username-input::placeholder {
  color: #3498db;
  font-weight: 500;
}

.email-input::placeholder {
  color: #e67e22;
  letter-spacing: 0.5px;
}

.password-input::placeholder {
  color: #e74c3c;
  font-size: 0.9em;
}

.message-textarea {
  min-height: 100px;
  resize: vertical;
}

.message-textarea::placeholder {
  color: #9b59b6;
  line-height: 1.6;
}

.search-input::placeholder {
  color: #2ecc71;
  font-weight: bold;
}

/* Creative form with animations */
.creative-form {
  margin-top: 2rem;
  padding: 2rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 12px;
}

.magic-input,
.magic-textarea {
  width: 100%;
  margin-bottom: 1rem;
  padding: 1rem;
  border: none;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.9);
  font-size: 1rem;
}

.magic-input::placeholder,
.magic-textarea::placeholder {
  color: #8e44ad;
  font-weight: 600;
  animation: placeholder-glow 3s ease-in-out infinite;
}

@keyframes placeholder-glow {
  0%,
  100% {
    opacity: 0.7;
  }
  50% {
    opacity: 1;
  }
}

.magic-input:focus::placeholder,
.magic-textarea:focus::placeholder {
  color: transparent;
}

/* Cross-browser placeholder support */
.modern-form input::-webkit-input-placeholder,
.modern-form textarea::-webkit-input-placeholder {
  color: #7f8c8d;
  font-style: italic;
}

.modern-form input::-moz-placeholder,
.modern-form textarea::-moz-placeholder {
  color: #7f8c8d;
  font-style: italic;
  opacity: 1;
}

.modern-form input:-ms-input-placeholder,
.modern-form textarea:-ms-input-placeholder {
  color: #7f8c8d;
  font-style: italic;
}

/* Responsive placeholder text */
@media (max-width: 768px) {
  .password-input::placeholder {
    content: 'รหัsผ่าน';
    font-size: 0.8em;
  }
}
```

## การใช้งานขั้นสูงและเทคนิคพิเศษ

### การรวม Pseudo-elements หลายตัว

```html
<!-- HTML -->
<div class="advanced-examples">
  <div class="card-complex">
    <h3>การ์ดที่ซับซ้อน</h3>
    <p>เนื้อหาในการ์ดที่มีเอฟเฟกต์หลายแบบ</p>
  </div>

  <blockquote class="fancy-quote">
    ความสำเร็จไม่ใช่จุดหมายปลายทาง แต่เป็นการเดินทางที่ไม่มีวันสิ้นสุด
  </blockquote>
</div>
```

```css
/* Complex card with multiple pseudo-elements */
.card-complex {
  position: relative;
  background: white;
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  margin: 2rem 0;
  overflow: hidden;
}

/* Background decoration */
.card-complex::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, #3498db, #e74c3c, #f39c12, #2ecc71);
}

/* Corner decoration */
.card-complex::after {
  content: '✨';
  position: absolute;
  top: 1rem;
  right: 1rem;
  font-size: 1.5rem;
  opacity: 0.3;
}

/* Title with underline effect */
.card-complex h3::after {
  content: '';
  display: block;
  width: 50px;
  height: 3px;
  background: #3498db;
  margin-top: 0.5rem;
  transition: width 0.3s ease;
}

.card-complex:hover h3::after {
  width: 100px;
}

/* Fancy quote with multiple decorations */
.fancy-quote {
  position: relative;
  font-size: 1.4rem;
  font-style: italic;
  text-align: center;
  padding: 3rem 2rem;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  border-radius: 12px;
  margin: 2rem 0;
  color: #2c3e50;
}

/* Opening quote mark */
.fancy-quote::before {
  content: '' ';
    position: absolute;
    top: 0.5rem;
    left: 1rem;
    font-size: 4rem;
    color: #3498db;
    line-height: 1;
    opacity: 0.7;
}

/* Closing quote mark */
.fancy-quote::after {
    content: ' '';
  position: absolute;
  bottom: 0.5rem;
  right: 1rem;
  font-size: 4rem;
  color: #3498db;
  line-height: 1;
  opacity: 0.7;
}

/* First letter styling */
.fancy-quote::first-letter {
  font-size: 2em;
  font-weight: bold;
  color: #e74c3c;
}
```

### CSS Counter กับ Pseudo-elements

```html
<!-- HTML -->
<div class="counter-examples">
  <ol class="custom-list">
    <li>รายการที่หนึ่ง</li>
    <li>รายการที่สอง</li>
    <li>รายการที่สาม</li>
    <li>รายการที่สี่</li>
  </ol>

  <div class="steps">
    <div class="step">วิเคราะห์ปัญหา</div>
    <div class="step">ออกแบบโซลูชัน</div>
    <div class="step">พัฒนาระบบ</div>
    <div class="step">ทดสอบและปรับปรุง</div>
  </div>
</div>
```

```css
/* Custom numbered list */
.custom-list {
  counter-reset: custom-counter;
  list-style: none;
  padding: 0;
}

.custom-list li {
  counter-increment: custom-counter;
  position: relative;
  padding: 1rem 1rem 1rem 4rem;
  margin-bottom: 0.5rem;
  background: #f8f9fa;
  border-radius: 8px;
  border-left: 4px solid #3498db;
}

.custom-list li::before {
  content: counter(custom-counter);
  position: absolute;
  left: 1rem;
  top: 50%;
  transform: translateY(-50%);
  background: #3498db;
  color: white;
  width: 2rem;
  height: 2rem;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 0.9rem;
}

/* Step indicators */
.steps {
  counter-reset: step-counter;
  display: flex;
  justify-content: space-between;
  margin: 2rem 0;
}

.step {
  counter-increment: step-counter;
  position: relative;
  flex: 1;
  text-align: center;
  padding: 2rem 1rem 1rem;
  background: #ecf0f1;
  margin: 0 0.5rem;
  border-radius: 8px;
}

.step::before {
  content: counter(step-counter);
  position: absolute;
  top: -1rem;
  left: 50%;
  transform: translateX(-50%);
  background: #2ecc71;
  color: white;
  width: 2rem;
  height: 2rem;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  border: 3px solid white;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

/* Connection lines between steps */
.step:not(:last-child)::after {
  content: '';
  position: absolute;
  top: -1rem;
  right: -0.5rem;
  width: 1rem;
  height: 2px;
  background: #bdc3c7;
  z-index: -1;
}

@media (max-width: 768px) {
  .steps {
    flex-direction: column;
  }

  .step {
    margin: 1rem 0;
  }

  .step:not(:last-child)::after {
    display: none;
  }
}
```

## Best Practices และข้อควรระวัง

### Performance Considerations

```css
/* ✅ ดี: ใช้ transform แทน position changes */
.element::before {
  transform: translateX(10px);
  transition: transform 0.3s ease;
}

/* ❌ หลีกเลี่ยง: การเปลี่ยน layout properties */
.element::before {
  left: 10px;
  transition: left 0.3s ease;
}

/* ✅ ดี: ใช้ will-change สำหรับ animations ที่ซับซ้อน */
.animated-element::before {
  will-change: transform, opacity;
}

.animated-element:not(:hover)::before {
  will-change: auto;
}
```

### Accessibility Guidelines

```css
/* ✅ ดี: เพิ่มข้อมูลที่มีความหมาย */
.important-note::before {
  content: '⚠️ ';
  speak: literal; /* Screen reader จะอ่านเครื่องหมาย */
}

/* ✅ ดี: ใช้ aria-label สำหรับข้อมูลสำคัญ */
.status[aria-label]::before {
  content: attr(aria-label) ': ';
}

/* ❌ หลีกเลี่ยง: เนื้อหาสำคัญใน pseudo-elements */
.bad-example::before {
  content: 'ข้อมูลสำคัญ'; /* Screen reader อาจพลาด */
}
```

### Browser Compatibility

```css
/* รองรับ browsers เก่า */
.element::before,
.element:before {
  /* Single colon สำหรับ IE8 */
  content: '';
  display: block;
}

/* Vendor prefixes สำหรับ properties พิเศษ */
.element::before {
  background: linear-gradient(45deg, red, blue);
  background: -webkit-linear-gradient(45deg, red, blue);
  background: -moz-linear-gradient(45deg, red, blue);
}
```

## สรุป

### Pseudo-elements สำคัญ 6 ตัว:

1. **::before** - เพิ่มเนื้อหาก่อน element
2. **::after** - เพิ่มเนื้อหาหลัง element
3. **::first-line** - จัดสไตล์บรรทัดแรก
4. **::first-letter** - จัดสไตล์ตัวอักษรแรก
5. **::selection** - จัดสไตล์ข้อความที่เลือก
6. **::placeholder** - จัดสไตล์ placeholder text

### หลักการใช้งาน:

- **content property** จำเป็นสำหรับ ::before และ ::after
- **ใช้สำหรับการตกแต่ง** ไม่ใช่เนื้อหาสำคัญ
- **รองรับ accessibility** ด้วยการใช้ที่เหมาะสม
- **optimize performance** ด้วย transform และ will-change
- **ทดสอบ cross-browser** สำหรับความเข้ากันได้

### ข้อควรระวัง:

- เนื้อหาใน pseudo-elements ไม่สามารถเลือกได้
- Screen readers อาจไม่อ่านเนื้อหาใน pseudo-elements
- ใช้ fallbacks สำหรับ browsers เก่า
- ระวัง performance ในการใช้ animations ที่ซับซ้อน

Pseudo-elements เป็นเครื่องมือที่ทรงพลังสำหรับการสร้าง UI ที่สวยงามและ interactive โดยไม่ต้องเพิ่ม markup ใน HTML!
