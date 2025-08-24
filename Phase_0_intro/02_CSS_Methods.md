# วิธีการแนบ CSS กับ HTML: 3 วิธีหลัก

## ภาพรวม

มี 3 วิธีหลักในการนำ CSS มาใช้กับหน้าเว็บ:

1. **Inline CSS** (style="") - ไม่แนะนำ
2. **Internal CSS** (`<style>`) - ใช้ในกรณีพิเศษ
3. **External CSS** (ไฟล์ .css) - **แนวปฏิบัติที่ดีที่สุด**

## 1. Inline CSS: การเขียน CSS ในแท็ก HTML

### วิธีการใช้งาน

```html
<element style="property: value; property: value;">เนื้อหา</element>
```

### ตัวอย่างการใช้งาน

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Inline CSS Example</title>
  </head>
  <body>
    <h1 style="color: red; font-size: 24px; text-align: center;">หัวข้อหลัก</h1>
    <p style="color: blue; font-family: Arial; margin: 20px;">
      นี่คือย่อหน้าที่ใช้ Inline CSS
    </p>
    <div
      style="background-color: yellow; padding: 15px; border: 2px solid black;"
    >
      กล่องข้อความ
    </div>
  </body>
</html>
```

### ข้อดีของ Inline CSS

- **ความเร็ว**: ไม่ต้องโหลดไฟล์เพิ่มเติม
- **ความเฉพาะเจาะจง**: มี specificity สูงสุด
- **การทดสอบเร็ว**: เหมาะสำหรับการทดสอบสไตล์ชั่วคราว

### ข้อเสียของ Inline CSS (เหตุผลที่หลีกเลี่ยง)

- **ผสมผสานกับ HTML**: ละเมิดหลักการแยกชั้น
- **ยากต่อการบำรุงรักษา**: ต้องแก้ไขในหลายจุด
- **ไม่สามารถใช้ซ้ำได้**: เขียนซ้ำหลายครั้ง
- **ขนาดไฟล์ใหญ่**: HTML บวม
- **ไม่รองรับ CSS ขั้นสูง**: ไม่มี pseudo-classes, media queries

```html
<!-- ❌ ไม่ดี: โค้ดซ้ำและยากแก้ไข -->
<h1 style="color: #2c3e50; font-size: 2rem; margin-bottom: 1rem;">หัวข้อ 1</h1>
<h1 style="color: #2c3e50; font-size: 2rem; margin-bottom: 1rem;">หัวข้อ 2</h1>
<h1 style="color: #2c3e50; font-size: 2rem; margin-bottom: 1rem;">หัวข้อ 3</h1>
```

## 2. Internal CSS: การเขียน CSS ในแท็ก `<style>`

### วิธีการใช้งาน

```html
<head>
  <style>
    selector {
      property: value;
    }
  </style>
</head>
```

### ตัวอย่างการใช้งาน

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Internal CSS Example</title>
    <style>
      body {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        line-height: 1.6;
        margin: 0;
        padding: 20px;
        background-color: #f4f4f4;
      }

      .header {
        background-color: #2c3e50;
        color: white;
        text-align: center;
        padding: 1rem;
        border-radius: 5px;
      }

      .content {
        background-color: white;
        padding: 20px;
        margin: 20px 0;
        border-radius: 5px;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      }

      .highlight {
        background-color: #f39c12;
        color: white;
        padding: 10px;
        border-radius: 3px;
      }

      /* Responsive Design */
      @media (max-width: 768px) {
        body {
          padding: 10px;
        }

        .header {
          font-size: 1.2rem;
        }
      }
    </style>
  </head>
  <body>
    <div class="header">
      <h1>หัวข้อหลัก</h1>
    </div>

    <div class="content">
      <p>เนื้อหาหลัก</p>
      <span class="highlight">ข้อความที่เน้น</span>
    </div>
  </body>
</html>
```

### ข้อดีของ Internal CSS

- **รวมในไฟล์เดียว**: ไม่ต้องโหลดไฟล์เพิ่ม
- **รองรับ CSS เต็มรูปแบบ**: pseudo-classes, media queries
- **เหมาะสำหรับหน้าเดียว**: การทดสอบหรือหน้าพิเศษ
- **โหลดเร็ว**: ไม่มี HTTP request เพิ่มเติม

### ข้อเสียของ Internal CSS

- **ไม่สามารถใช้ซ้ำได้**: จำกัดเฉพาะหน้านั้น
- **ขนาดไฟล์ HTML ใหญ่**: CSS ผสมกับ HTML
- **ไม่มี cache**: โหลดใหม่ทุกครั้งที่เข้าหน้า
- **ยากต่อการจัดการ**: เมื่อมีหลายหน้า

### เมื่อไหร่ควรใช้ Internal CSS

```html
<!-- ✅ เหมาะสำหรับ: -->
<!-- 1. หน้าเดียวที่มีสไตล์พิเศษ -->
<!-- 2. Email templates -->
<!-- 3. การทดสอบเร็ว -->
<!-- 4. Critical CSS สำหรับ above-the-fold content -->

<style>
  /* Critical CSS สำหรับส่วนที่เห็นก่อน */
  .hero {
    height: 100vh;
    background: linear-gradient(45deg, #667eea 0%, #764ba2 100%);
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>
```

## 3. External CSS: ไฟล์ .css แยกต่างหาก (แนวปฏิบัติหลัก)

### วิธีการใช้งาน

```html
<head>
  <link rel="stylesheet" href="path/to/stylesheet.css" />
</head>
```

### โครงสร้างไฟล์

```
project/
├── index.html
├── about.html
├── contact.html
└── css/
    ├── main.css
    ├── responsive.css
    └── components.css
```

### ตัวอย่างการใช้งาน

**index.html**

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>External CSS Example</title>

    <!-- External CSS Files -->
    <link rel="stylesheet" href="css/main.css" />
    <link rel="stylesheet" href="css/components.css" />
    <link rel="stylesheet" href="css/responsive.css" />
  </head>
  <body>
    <header class="header">
      <nav class="navbar">
        <div class="logo">My Website</div>
        <ul class="nav-menu">
          <li><a href="#home" class="nav-link">หน้าแรก</a></li>
          <li><a href="#about" class="nav-link">เกี่ยวกับ</a></li>
          <li><a href="#contact" class="nav-link">ติดต่อ</a></li>
        </ul>
      </nav>
    </header>

    <main class="main-content">
      <section class="hero">
        <h1 class="hero-title">ยินดีต้อนรับ</h1>
        <p class="hero-subtitle">เว็บไซต์ที่ใช้ External CSS</p>
        <button class="btn btn-primary">เริ่มต้น</button>
      </section>
    </main>
  </body>
</html>
```

**css/main.css**

```css
/* Reset และ Base Styles */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  line-height: 1.6;
  color: #333;
}

/* Layout */
.header {
  background-color: #2c3e50;
  color: white;
  padding: 1rem 0;
  position: fixed;
  width: 100%;
  top: 0;
  z-index: 1000;
}

.main-content {
  margin-top: 80px;
}

.hero {
  height: 100vh;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: white;
}

.hero-title {
  font-size: 3rem;
  margin-bottom: 1rem;
  animation: fadeInUp 1s ease-out;
}

.hero-subtitle {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  animation: fadeInUp 1s ease-out 0.3s both;
}

/* Animations */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
```

**css/components.css**

```css
/* Navigation */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
}

.nav-menu {
  display: flex;
  list-style: none;
  gap: 2rem;
}

.nav-link {
  color: white;
  text-decoration: none;
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: #3498db;
}

/* Buttons */
.btn {
  padding: 12px 24px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1rem;
  transition: all 0.3s ease;
}

.btn-primary {
  background-color: #3498db;
  color: white;
}

.btn-primary:hover {
  background-color: #2980b9;
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}
```

**css/responsive.css**

```css
/* Tablet */
@media (max-width: 768px) {
  .navbar {
    flex-direction: column;
    gap: 1rem;
  }

  .nav-menu {
    gap: 1rem;
  }

  .hero-title {
    font-size: 2rem;
  }

  .main-content {
    margin-top: 120px;
  }
}

/* Mobile */
@media (max-width: 480px) {
  .navbar {
    padding: 0 1rem;
  }

  .nav-menu {
    flex-direction: column;
    gap: 0.5rem;
  }

  .hero {
    padding: 0 1rem;
  }

  .hero-title {
    font-size: 1.5rem;
  }

  .hero-subtitle {
    font-size: 1rem;
  }
}
```

### ข้อดีของ External CSS (เหตุผลที่เป็นแนวปฏิบัติหลัก)

#### 1. **การแยกชั้นที่สมบูรณ์**

```html
<!-- HTML เน้นโครงสร้าง -->
<article class="blog-post">
  <h1 class="post-title">หัวข้อบทความ</h1>
  <p class="post-content">เนื้อหา...</p>
</article>
```

#### 2. **การใช้ซ้ำได้ (Reusability)**

```html
<!-- หลายหน้าใช้ CSS เดียวกัน -->
<!-- index.html -->
<link rel="stylesheet" href="css/main.css" />

<!-- about.html -->
<link rel="stylesheet" href="css/main.css" />

<!-- contact.html -->
<link rel="stylesheet" href="css/main.css" />
```

#### 3. **การจัดการง่าย (Maintainability)**

```css
/* แก้ไขที่เดียว ส่งผลทุกหน้า */
.primary-color {
  color: #3498db; /* เปลี่ยนสีหลักที่เดียว */
}
```

#### 4. **ประสิทธิภาพ (Performance)**

```html
<!-- Browser cache ไฟล์ CSS -->
<link rel="stylesheet" href="css/main.css" />
<!-- จะ cache -->
<!-- การโหลดหน้าต่อไปจะเร็วขึ้น -->
```

#### 5. **การทำงานเป็นทีม**

```
team-workflow/
├── designer/
│   └── styles.css      # นักออกแบบแก้ไข
├── developer/
│   ├── index.html      # นักพัฒนาแก้ไข
│   └── script.js
└── shared/
    └── main.css        # ไฟล์ที่แชร์
```

### เทคนิคการใช้ External CSS อย่างมีประสิทธิภาพ

#### 1. **การจัดระเบียบไฟล์**

```css
/* main.css - โครงสร้างหลัก */
@import url('reset.css');
@import url('typography.css');
@import url('layout.css');
@import url('components.css');
@import url('utilities.css');
```

#### 2. **การโหลดแบบ Conditional**

```html
<!-- โหลดตามเงื่อนไข -->
<link rel="stylesheet" href="css/print.css" media="print" />
<link
  rel="stylesheet"
  href="css/mobile.css"
  media="screen and (max-width: 768px)"
/>
```

#### 3. **การเพิ่มประสิทธิภาพ**

```html
<!-- Preload สำหรับไฟล์สำคัญ -->
<link rel="preload" href="css/critical.css" as="style" />
<link rel="stylesheet" href="css/critical.css" />

<!-- Async loading สำหรับไฟล์ไม่สำคัญ -->
<link
  rel="preload"
  href="css/non-critical.css"
  as="style"
  onload="this.onload=null;this.rel='stylesheet'"
/>
```

## เปรียบเทียบทั้ง 3 วิธี

| เกณฑ์             | Inline         | Internal       | External       |
| ----------------- | -------------- | -------------- | -------------- |
| **การแยกชั้น**    | ❌ ไม่แยก      | ⚠️ แยกบางส่วน  | ✅ แยกสมบูรณ์  |
| **การใช้ซ้ำ**     | ❌ ไม่ได้      | ⚠️ หน้าเดียว   | ✅ หลายหน้า    |
| **การบำรุงรักษา** | ❌ ยาก         | ⚠️ ปานกลาง     | ✅ ง่าย        |
| **ประสิทธิภาพ**   | ⚠️ ไม่มี cache | ⚠️ ไม่มี cache | ✅ มี cache    |
| **ขนาดไฟล์**      | ❌ HTML บวม    | ❌ HTML บวม    | ✅ แยกโหลด     |
| **ความเร็วโหลด**  | ✅ เร็ว        | ✅ เร็ว        | ⚠️ ช้าครั้งแรก |
| **การทำงานทีม**   | ❌ ยาก         | ❌ ยาก         | ✅ ง่าย        |

## คำแนะนำการใช้งาน

### ✅ ใช้ External CSS เมื่อ:

- พัฒนาเว็บไซต์ที่มีหลายหน้า
- ทำงานเป็นทีม
- ต้องการบำรุงรักษาระยะยาว
- สร้าง Design System

### ⚠️ ใช้ Internal CSS เมื่อ:

- หน้าเดียวที่มีสไตล์พิเศษ
- Email templates
- Critical CSS สำหรับ performance
- การทดสอบเร็ว

### ❌ หลีกเลี่ยง Inline CSS เว้นแต่:

- การ override ชั่วคราว
- JavaScript สร้างสไตล์แบบไดนามิก
- การทดสอบจุดเดียว

## สรุป

**External CSS** เป็น**แนวปฏิบัติที่ดีที่สุด**เพราะ:

1. **แยกชั้นสมบูรณ์**: HTML, CSS, JS แยกกันชัดเจน
2. **ใช้ซ้ำได้**: หลายหน้าใช้ไฟล์เดียว
3. **บำรุงรักษาง่าย**: แก้ไขที่เดียว ได้ผลทุกหน้า
4. **ประสิทธิภาพดี**: Browser cache ทำให้โหลดเร็ว
5. **ทำงานทีมได้**: แยกหน้าที่ชัดเจน

การเริ่มต้นควรใช้ External CSS ตั้งแต่โปรเจกต์แรก เพื่อสร้างนิสัยที่ดีและรองรับการขยายงานในอนาคต
