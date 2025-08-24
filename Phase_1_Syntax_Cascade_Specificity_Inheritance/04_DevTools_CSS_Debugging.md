# เครื่องมือ DevTools สำหรับ Debug CSS

## ภาพรวม DevTools

DevTools (Developer Tools) เป็นเครื่องมือที่มีอยู่ในเบราว์เซอร์ทุกตัว ช่วยให้นักพัฒนาสามารถตรวจสอบ แก้ไข และ debug HTML, CSS, JavaScript ได้แบบ real-time โดยไม่ต้องแก้ไขไฟล์ต้นฉบับ

### การเปิด DevTools

#### วิธีการเปิด:

```
1. คลิกขวาบนหน้าเว็บ → เลือก "Inspect" หรือ "ตรวจสอบองค์ประกอบ"
2. กดคีย์ F12
3. กด Ctrl+Shift+I (Windows/Linux) หรือ Cmd+Option+I (Mac)
4. เมนู Browser → More Tools → Developer Tools
```

### ส่วนประกอบหลักของ DevTools

#### 1. Elements Panel (แผง Elements)

- แสดงโครงสร้าง HTML
- แสดง CSS styles ที่ใช้งาน
- แก้ไข HTML/CSS แบบ live

#### 2. Console Panel (แผง Console)

- แสดง error และ warning
- รัน JavaScript command

#### 3. Sources Panel (แผง Sources)

- ดูไฟล์ต้นฉบับ
- debug JavaScript

#### 4. Network Panel (แผง Network)

- ดูการโหลดไฟล์ต่างๆ
- ตรวจสอบความเร็วในการโหลด

## การใช้ Inspect Element

### ขั้นตอนการ Inspect

#### 1. เลือก Element

```html
<!-- ตัวอย่าง HTML -->
<div class="container">
  <h1 id="main-title" class="title highlight">หัวข้อหลัก</h1>
  <p class="content">เนื้อหาบทความ</p>
</div>
```

**วิธีเลือก Element:**

- คลิกขวาบน element → "Inspect"
- กดปุ่ม "Select an element" (ไอคอนลูกศร) แล้วคลิกบน element
- ใช้ Ctrl+Shift+C แล้วคลิกบน element

#### 2. ดูโครงสร้าง HTML

```html
<!-- ใน Elements panel จะเห็น -->
<body>
  <div class="container">
    <h1 id="main-title" class="title highlight">หัวข้อหลัก</h1>
    ← element ที่เลือก
    <p class="content">เนื้อหาบทความ</p>
  </div>
</body>
```

**คุณสมบัติใน Elements panel:**

- Element ที่เลือกจะถูก highlight
- สามารถขยาย/ยุบ element ได้
- แก้ไข HTML ได้แบบ live
- ดู attributes ต่างๆ

### การแก้ไข HTML แบบ Live

#### 1. แก้ไข Text Content

```html
<!-- Double click บนข้อความเพื่อแก้ไข -->
<h1>หัวข้อเดิม</h1>
<!-- เปลี่ยนเป็น -->
<h1>หัวข้อใหม่</h1>
```

#### 2. แก้ไข Attributes

```html
<!-- คลิกขวาบน element → Edit Attribute -->
<h1 class="title">หัวข้อ</h1>
<!-- เปลี่ยนเป็น -->
<h1 class="title new-class">หัวข้อ</h1>
```

#### 3. เพิ่ม/ลบ Element

```html
<!-- คลิกขวา → Delete element -->
<!-- คลิกขวา → Edit as HTML -->
```

## การดู CSS Styles

### Styles Panel (แผงสไตล์)

ใน Elements panel ทางด้านขวาจะมี Styles panel แสดง CSS ที่เกี่ยวข้องกับ element ที่เลือก

#### 1. โครงสร้างของ Styles Panel

```css
/* ตัวอย่างที่แสดงใน Styles panel */

element.style {
  /* Inline styles (ถ้ามี) */
  color: red;
}

#main-title.title.highlight {
  /* CSS rules ที่มีผล */
  font-size: 2rem;
  color: blue; /* ถูกขีดฆ่า เพราะ inline style override */
}

.title {
  /* CSS rules ที่ถูก override */
  color: green; /* ถูกขีดฆ่า */
  font-weight: bold;
}

h1 {
  /* Browser default styles */
  display: block;
  font-size: 2em; /* ถูกขีดฆ่า */
  margin-block-start: 0.67em;
}
```

#### 2. การอ่าน Styles Panel

- **ไม่มีขีดฆ่า** = CSS rule ที่มีผล
- **มีขีดฆ่า** = CSS rule ที่ถูก override
- **เรียงจากบนลงล่าง** = ลำดับ specificity จากสูงไปต่ำ

### การแก้ไข CSS แบบ Live

#### 1. เปลี่ยนค่า Property

```css
/* คลิกบนค่า property เพื่อแก้ไข */
.title {
  color: blue; /* คลิกบน "blue" เพื่อเปลี่ยน */
  font-size: 2rem; /* คลิกบน "2rem" เพื่อเปลี่ยน */
}
```

#### 2. เพิ่ม Property ใหม่

```css
/* คลิกบนบรรทัดว่างใน CSS rule */
.title {
  color: blue;
  /* คลิกตรงนี้เพื่อเพิ่ม property ใหม่ */
}
```

#### 3. ปิด/เปิด Property

```css
/* คลิกบน checkbox ข้าง property */
.title {
    ☑ color: blue;      /* เปิดใช้งาน */
    ☐ font-size: 2rem;  /* ปิดใช้งาน */
}
```

#### 4. เพิ่ม CSS Rule ใหม่

```css
/* คลิกปุ่ม "+" หรือ "New Style Rule" */
/* จะสร้าง rule ใหม่ตาม element ที่เลือก */
.new-class {
  /* เพิ่ม properties ตรงนี้ */
}
```

## Computed Styles (สไตล์ที่คำนวณแล้ว)

### ความหมายของ Computed Styles

Computed Styles คือค่าสุดท้ายของ CSS properties หลังจากที่เบราว์เซอร์คำนวณจาก:

- CSS rules ทั้งหมด
- Inheritance
- Cascade และ Specificity
- Browser default styles

### การเข้าถึง Computed Panel

#### ใน DevTools:

1. เลือก element ใน Elements panel
2. คลิกแท็บ "Computed" ข้าง "Styles"
3. หรือเลื่อนลงมาใน Styles panel

### การอ่าน Computed Styles

```css
/* ตัวอย่าง Computed styles */

color: rgb(255, 0, 0)
├─ element.style
├─ .title { color: red; }

font-size: 32px
├─ .title { font-size: 2rem; }
└─ Inherited from body { font-size: 16px; }

margin: 0px
├─ h1 { margin: 0; }
└─ user agent stylesheet

display: block
└─ user agent stylesheet
```

#### คุณสมบัติของ Computed panel:

- **แสดงค่าสุดท้าย** ที่เบราว์เซอร์ใช้จริง
- **แปลงหน่วย** (เช่น rem → px)
- **แสดงแหล่งที่มา** ของแต่ละค่า
- **เรียงตาม alphabetical** order

### การใช้ Filter ใน Computed

```css
/* พิมพ์ใน search box ของ Computed panel */

"color"     → แสดงเฉพาะ properties ที่เกี่ยวกับสี
"margin"    → แสดงเฉพาะ margin properties
"font"      → แสดงเฉพาะ font properties
"inherited" → แสดงเฉพาะ properties ที่สืบทอด
```

## Exercise: 3 CSS Rules ที่ทับกัน

### โจทย์: สร้างไฟล์ทดสอบ

สร้างไฟล์ `debug-exercise.html` และ `debug-styles.css`:

#### debug-exercise.html

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CSS Debugging Exercise</title>
    <link rel="stylesheet" href="debug-styles.css" />
    <style>
      /* Internal CSS - Rule 2 */
      #main-heading {
        color: green;
        font-size: 28px;
        text-decoration: underline;
      }

      .primary-title {
        color: blue;
        font-weight: normal;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <h1
        id="main-heading"
        class="primary-title highlight"
        style="color: red; font-weight: bold;"
      >
        หัวข้อสำคัญ
      </h1>
      <p class="description">
        ใช้ DevTools เพื่อตรวจสอบว่า CSS rule ไหนมีผลสุดท้าย
      </p>
    </div>
  </body>
</html>
```

#### debug-styles.css

```css
/* External CSS - Rule 1 */

/* Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  line-height: 1.6;
  padding: 2rem;
  background-color: #f8f9fa;
}

.container {
  max-width: 800px;
  margin: 0 auto;
  background: white;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

/* CSS Rules ที่ทับกัน */

/* Rule 1: Element selector */
h1 {
  color: black;
  font-size: 24px;
  font-weight: normal;
  margin-bottom: 1rem;
}

/* Rule 2: Class selector */
.primary-title {
  color: purple;
  font-size: 26px;
  font-weight: bold;
  text-transform: uppercase;
}

/* Rule 3: ID selector */
#main-heading {
  color: orange;
  font-size: 30px;
  font-style: italic;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

/* Rule 4: Multiple class selector */
.primary-title.highlight {
  color: navy;
  font-size: 32px;
  background-color: yellow;
}

/* Rule 5: ID + Class selector */
#main-heading.primary-title {
  color: darkgreen;
  font-size: 34px;
  border: 2px solid #ccc;
}

.description {
  color: #666;
  margin-top: 2rem;
  padding: 1rem;
  background-color: #f8f9fa;
  border-left: 4px solid #007bff;
}
```

### การวิเคราะห์ด้วย DevTools

#### ขั้นตอนที่ 1: เปิดไฟล์และ Inspect

1. เปิดไฟล์ `debug-exercise.html` ในเบราว์เซอร์
2. คลิกขวาบนหัวข้อ "หัวข้อสำคัญ" → Inspect
3. ดู Styles panel ทางขวา

#### ขั้นตอนที่ 2: วิเคราะห์ใน Styles Panel

```css
/* สิ่งที่จะเห็นใน Styles panel (เรียงจากบนลงล่าง) */

element.style {
  color: red; /* ✅ มีผล - inline style */
  font-weight: bold; /* ✅ มีผล - inline style */
}

#main-heading.primary-title {
  color: darkgreen; /* ❌ ถูกขีดฆ่า - แพ้ inline */
  font-size: 34px; /* ✅ มีผล - specificity สูงสุด */
  border: 2px solid #ccc; /* ✅ มีผล */
}

.primary-title.highlight {
  color: navy; /* ❌ ถูกขีดฆ่า */
  font-size: 32px; /* ❌ ถูกขีดฆ่า */
  background-color: yellow; /* ✅ มีผล */
}

#main-heading {
  color: orange; /* ❌ ถูกขีดฆ่า */
  font-size: 30px; /* ❌ ถูกขีดฆ่า */
  font-style: italic; /* ✅ มีผล */
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3); /* ✅ มีผล */
}

.primary-title {
  color: blue; /* ❌ ถูกขีดฆ่า - จาก internal CSS */
  font-weight: normal; /* ❌ ถูกขีดฆ่า - จาก internal CSS และ inline */
}

.primary-title {
  color: purple; /* ❌ ถูกขีดฆ่า - จาก external CSS */
  font-size: 26px; /* ❌ ถูกขีดฆ่า */
  font-weight: bold; /* ❌ ถูกขีดฆ่า */
  text-transform: uppercase; /* ✅ มีผล */
}

h1 {
  color: black; /* ❌ ถูกขีดฆ่า */
  font-size: 24px; /* ❌ ถูกขีดฆ่า */
  font-weight: normal; /* ❌ ถูกขีดฆ่า */
  margin-bottom: 1rem; /* ✅ มีผล */
}
```

#### ขั้นตอนที่ 3: ดู Computed Styles

คลิกแท็บ "Computed" เพื่อดูค่าสุดท้าย:

```css
/* Computed Styles */

color: rgb(255, 0, 0)              /* red จาก inline style */
├─ element.style

font-size: 34px                    /* จาก #main-heading.primary-title */
├─ #main-heading.primary-title {
  font-size: 34px;
}

font-weight: 700                   /* bold จาก inline style */
├─ element.style

font-style: italic                 /* จาก #main-heading */
├─ #main-heading {
  font-style: italic;
}

background-color: rgb(255, 255, 0) /* yellow จาก .primary-title.highlight */
├─ .primary-title.highlight {
  background-color: yellow;
}

text-transform: uppercase          /* จาก .primary-title */
├─ .primary-title {
  text-transform: uppercase;
}

border: 2px solid rgb(204, 204, 204) /* จาก #main-heading.primary-title */
├─ #main-heading.primary-title {
  border: 2px solid #ccc;
}
```

### การวิเคราะห์ Specificity

#### คำนวณ Specificity ของแต่ละ Rule:

```css
/* รูปแบบ: (inline, id, class, element) */

/* 1. inline style="color: red; font-weight: bold;" */
/* Specificity: (1, 0, 0, 0) = 1000 - ชนะทุกอย่าง */

/* 2. #main-heading.primary-title */
/* Specificity: (0, 1, 1, 0) = 110 */

/* 3. .primary-title.highlight */
/* Specificity: (0, 0, 2, 0) = 20 */

/* 4. #main-heading */
/* Specificity: (0, 1, 0, 0) = 100 */

/* 5. .primary-title (internal CSS) */
/* Specificity: (0, 0, 1, 0) = 10 - แต่มาทีหลัง */

/* 6. .primary-title (external CSS) */
/* Specificity: (0, 0, 1, 0) = 10 - มาก่อน */

/* 7. h1 */
/* Specificity: (0, 0, 0, 1) = 1 */
```

### คำตอบ: อะไรมีผลสุดท้ายและเพราะอะไร

#### Properties ที่มีผลสุดท้าย:

1. **color: red**

   - **แหล่งที่มา:** inline style
   - **เหตุผล:** inline style มี specificity สูงสุด (1000)

2. **font-size: 34px**

   - **แหล่งที่มา:** `#main-heading.primary-title`
   - **เหตุผล:** specificity (110) สูงกว่า rules อื่น

3. **font-weight: bold**

   - **แหล่งที่มา:** inline style
   - **เหตุผล:** inline style มี specificity สูงสุด

4. **font-style: italic**

   - **แหล่งที่มา:** `#main-heading`
   - **เหตุผล:** เป็น property เดียวที่กำหนด ไม่มีการแข่งขัน

5. **background-color: yellow**

   - **แหล่งที่มา:** `.primary-title.highlight`
   - **เหตุผล:** เป็น property เดียวที่กำหนด

6. **text-transform: uppercase**

   - **แหล่งที่มา:** `.primary-title`
   - **เหตุผล:** เป็น property เดียวที่กำหนด

7. **border: 2px solid #ccc**
   - **แหล่งที่มา:** `#main-heading.primary-title`
   - **เหตุผล:** เป็น property เดียวที่กำหนด

#### สรุปหลักการ:

1. **Inline styles ชนะทุกอย่าง** (ยกเว้น !important)
2. **Specificity สูงกว่าชนะ** เมื่อไม่มี inline style
3. **CSS ที่มาทีหลังชนะ** เมื่อ specificity เท่ากัน
4. **Properties ที่ไม่แข่งขันกัน** จะมีผลทั้งหมด

## เทคนิคการ Debug ขั้นสูง

### 1. ใช้ Element States

```css
/* ทดสอบ pseudo-classes */
/* ใน Styles panel คลิก ":hov" */
/* เลือก :hover, :focus, :active, :visited */

.primary-title:hover {
  color: lime;
  transform: scale(1.1);
}

.primary-title:focus {
  outline: 3px solid blue;
}
```

### 2. ใช้ Device Emulation

```css
/* ทดสอบ responsive design */
/* คลิกไอคอน device toggle */
/* เลือก device หรือกำหนดขนาดเอง */

@media (max-width: 768px) {
  .primary-title {
    font-size: 20px;
  }
}
```

### 3. Performance และ Coverage

```css
/* ดู CSS ที่ไม่ได้ใช้ */
/* เปิดแท็บ Coverage */
/* คลิก record และโหลดหน้า */
/* จะเห็น CSS ที่ไม่ได้ใช้เป็นสีแดง */
```

### 4. Console Commands

```javascript
// รัน command ใน Console

// ดู computed styles
getComputedStyle(document.querySelector('#main-heading')).color;

// เปลี่ยน style แบบ temporary
document.querySelector('#main-heading').style.color = 'purple';

// ดู CSS rules
[...document.styleSheets[0].cssRules].forEach((rule) =>
  console.log(rule.cssText)
);
```

## Best Practices สำหรับการใช้ DevTools

### 1. การจัดระเบียบการ Debug

```css
/* ✅ ใช้ comments เพื่อ debug */
.debug-element {
  /* TODO: ทำไม margin ไม่ทำงาน? */
  margin: 20px;

  /* FIXME: สีไม่เปลี่ยนตาม design */
  color: red;

  /* DEBUG: ทดสอบ border */
  border: 1px solid lime;
}
```

### 2. ใช้ Console Log

```javascript
// Debug CSS values
console.log('Color:', getComputedStyle(element).color);
console.log('Font size:', getComputedStyle(element).fontSize);

// Debug specificity
console.log('Element classes:', element.classList);
console.log('Element ID:', element.id);
```

### 3. สร้าง Debug CSS

```css
/* ไฟล์ debug.css แยกต่างหาก */
.debug-red {
  border: 2px solid red !important;
}
.debug-blue {
  border: 2px solid blue !important;
}
.debug-green {
  border: 2px solid green !important;
}

.debug-bg-red {
  background: rgba(255, 0, 0, 0.2) !important;
}
.debug-bg-blue {
  background: rgba(0, 0, 255, 0.2) !important;
}

/* เพิ่ม class เหล่านี้ใน HTML เพื่อ debug */
```

## สรุป

### เครื่องมือสำคัญใน DevTools:

- **Elements Panel** - ดูและแก้ไข HTML/CSS
- **Styles Panel** - ดู CSS rules และ cascade
- **Computed Panel** - ดูค่าสุดท้ายหลัง calculation
- **Console** - รัน JavaScript commands

### หลักการ Debug CSS:

1. **Inspect element** เพื่อดูโครงสร้าง
2. **ดู Styles panel** เพื่อเข้าใจ cascade
3. **ดู Computed styles** เพื่อยืนยันค่าสุดท้าย
4. **ทดสอบแก้ไข** แบบ live
5. **คัดลอกไปใส่ไฟล์จริง**

### การแก้ปัญหา CSS:

- ตรวจสอบ **Specificity** และ **Cascade**
- ดู **Inheritance** ใน Computed styles
- ใช้ **!important** เฉพาะเมื่อจำเป็น
- ทดสอบใน **responsive modes**

DevTools เป็นเครื่องมือที่ทรงพลังที่จะช่วยให้การเขียนและ debug CSS เป็นเรื่องง่ายขึ้นมาก!
