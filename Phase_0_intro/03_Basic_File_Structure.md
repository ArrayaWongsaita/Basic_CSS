# โครงสร้างไฟล์พื้นฐาน: index.html + styles.css

## โครงสร้างโปรเจกต์พื้นฐาน

การสร้างเว็บไซต์ด้วย HTML และ CSS เริ่มต้นจากการจัดโครงสร้างไฟล์ที่เป็นระเบียบ

### โครงสร้างโฟลเดอร์แนะนำ

```
my-website/
├── index.html          # หน้าหลักของเว็บไซต์
├── styles.css          # ไฟล์ CSS หลัก
├── css/               # โฟลเดอร์สำหรับไฟล์ CSS (ทางเลือก)
│   ├── main.css
│   └── responsive.css
├── images/            # โฟลเดอร์สำหรับรูปภาพ
│   ├── logo.png
│   └── hero.jpg
└── js/                # โฟลเดอร์สำหรับ JavaScript
    └── script.js
```

### ทำไมต้อง index.html?

- **มาตรฐานเว็บเซิร์ฟเวอร์**: เซิร์ฟเวอร์จะหา index.html เป็นหน้าแรก
- **URL สะอาด**: `example.com/` แทน `example.com/home.html`
- **ง่ายต่อการจำ**: เป็นชื่อมาตรฐานที่ทุกคนรู้จัก

## ไฟล์ index.html พื้นฐาน

### โครงสร้างพื้นฐาน

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>หน้าแรก - เว็บไซต์ของฉัน</title>

    <!-- ลิงก์ไฟล์ CSS -->
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <!-- เนื้อหาหน้าเว็บ -->
    <header>
      <h1>ยินดีต้อนรับสู่เว็บไซต์ของฉัน</h1>
      <nav>
        <ul>
          <li><a href="#home">หน้าแรก</a></li>
          <li><a href="#about">เกี่ยวกับ</a></li>
          <li><a href="#contact">ติดต่อ</a></li>
        </ul>
      </nav>
    </header>

    <main>
      <section id="home">
        <h2>เนื้อหาหลัก</h2>
        <p>ข้อความในหน้าแรก</p>
      </section>
    </main>

    <footer>
      <p>&copy; 2024 เว็บไซต์ของฉัน</p>
    </footer>
  </body>
</html>
```

### องค์ประกอบสำคัญใน index.html

#### 1. DOCTYPE และ HTML Tag

```html
<!DOCTYPE html>
<!-- บอกเบราว์เซอร์ว่าเป็น HTML5 -->
<html lang="th">
  <!-- ภาษาไทย -->
</html>
```

#### 2. Head Section

```html
<head>
  <meta charset="UTF-8" />
  <!-- การเข้ารหัสภาษาไทย -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <!-- Responsive -->
  <title>หน้าแรก - เว็บไซต์ของฉัน</title>
  <!-- ชื่อแท็บเบราว์เซอร์ -->

  <!-- การลิงก์ไฟล์ CSS -->
  <link rel="stylesheet" href="styles.css" />
</head>
```

#### 3. Body Structure

```html
<body>
    <header>    <!-- ส่วนหัวเว็บไซต์ -->
    <nav>       <!-- เมนูนำทาง -->
    <main>      <!-- เนื้อหาหลัก -->
    <section>   <!-- ส่วนต่างๆ ของเนื้อหา -->
    <footer>    <!-- ส่วนท้ายเว็บไซต์ -->
</body>
```

## ไฟล์ styles.css พื้นฐาน

### โครงสร้าง CSS พื้นฐาน

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

/* Header Styles */
header {
  background-color: #2c3e50;
  color: white;
  padding: 1rem;
  text-align: center;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

/* Navigation Styles */
nav ul {
  list-style: none;
  display: flex;
  justify-content: center;
  gap: 2rem;
}

nav a {
  color: white;
  text-decoration: none;
  transition: color 0.3s ease;
}

nav a:hover {
  color: #3498db;
}

/* Main Content */
main {
  max-width: 1200px;
  margin: 2rem auto;
  padding: 0 1rem;
}

section {
  margin-bottom: 2rem;
}

h2 {
  color: #2c3e50;
  margin-bottom: 1rem;
}

/* Footer */
footer {
  background-color: #34495e;
  color: white;
  text-align: center;
  padding: 1rem;
  margin-top: 2rem;
}
```

### การจัดระเบียบ CSS

#### 1. ความคิดเห็น (Comments)

```css
/* ==========================================================================
   Header Styles
   ========================================================================== */

/* Navigation */
nav {
  /* สไตล์เมนู */
}

/* Button Components */
.btn {
  /* สไตล์ปุ่ม */
}
```

#### 2. การเรียงลำดับ Properties

```css
.element {
  /* Position */
  position: relative;
  top: 0;
  left: 0;

  /* Display & Box Model */
  display: block;
  width: 100px;
  height: 100px;
  margin: 10px;
  padding: 10px;

  /* Typography */
  font-family: Arial;
  font-size: 16px;
  color: #333;

  /* Visual */
  background-color: #fff;
  border: 1px solid #ccc;

  /* Misc */
  transition: all 0.3s ease;
}
```

## Exercise: แนบ styles.css และเปลี่ยนสี h1

### ขั้นตอนที่ 1: สร้างโครงสร้างไฟล์

สร้างโฟลเดอร์ใหม่ชื่อ `my-first-website` และสร้างไฟล์ 2 ไฟล์:

```
my-first-website/
├── index.html
└── styles.css
```

### ขั้นตอนที่ 2: สร้างไฟล์ index.html

สร้างไฟล์ `index.html` และใส่โค้ดนี้:

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>การทดสอบ CSS</title>

    <!-- TODO: ใส่ลิงก์ไฟล์ CSS ตรงนี้ -->
  </head>
  <body>
    <header>
      <h1>หัวข้อหลักของเว็บไซต์</h1>
      <h1 class="special-title">หัวข้อพิเศษ</h1>
    </header>

    <main>
      <h2>หัวข้อรอง</h2>
      <p>นี่คือย่อหน้าทดสอบ</p>

      <section>
        <h1 id="unique-title">หัวข้อที่มี ID</h1>
        <p class="highlight">ข้อความที่เน้น</p>
      </section>
    </main>
  </body>
</html>
```

### ขั้นตอนที่ 3: สร้างไฟล์ styles.css

สร้างไฟล์ `styles.css` (ยังไม่ใส่เนื้อหา):

```css
/* ไฟล์ CSS สำหรับทดสอบ */

/* TODO: ใส่สไตล์ CSS ตรงนี้ */
```

### ขั้นตอนที่ 4: ลิงก์ไฟล์ CSS

**แก้ไข index.html** โดยเพิ่มบรรทัดนี้ใน `<head>`:

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>การทดสอบ CSS</title>

  <!-- ลิงก์ไฟล์ CSS -->
  <link rel="stylesheet" href="styles.css" />
</head>
```

### ขั้นตอนที่ 5: ทดสอบการเชื่อมต่อ

เพิ่มโค้ดนี้ใน `styles.css` เพื่อทดสอบ:

```css
/* ทดสอบการเชื่อมต่อ CSS */
body {
  background-color: #f0f0f0;
  font-family: Arial, sans-serif;
}

/* ถ้าพื้นหลังเปลี่ยนเป็นสีเทาอ่อน แสดงว่าเชื่อมต่อสำเร็จ */
```

**วิธีทดสอบ:**

1. เปิดไฟล์ `index.html` ในเบราว์เซอร์
2. ถ้าพื้นหลังเป็นสีเทาอ่อน = เชื่อมต่อสำเร็จ ✅
3. ถ้าพื้นหลังยังเป็นสีขาว = เชื่อมต่อไม่สำเร็จ ❌

### ขั้นตอนที่ 6: เปลี่ยนสี h1 แบบละเอียด

#### 6.1 เปลี่ยนสี h1 ทั้งหมด

```css
/* เปลี่ยนสี h1 ทั้งหมดเป็นสีแดง */
h1 {
  color: red;
}
```

**ผลลัพธ์:** h1 ทั้งหมดจะเป็นสีแดง

#### 6.2 เปลี่ยนสี h1 เฉพาะ class

```css
/* เปลี่ยนสี h1 ทั้งหมดเป็นสีน้ำเงิน */
h1 {
  color: blue;
}

/* เปลี่ยนสี h1 ที่มี class="special-title" เป็นสีเขียว */
h1.special-title {
  color: green;
}
```

**ผลลัพธ์:**

- h1 ปกติ = สีน้ำเงิน
- h1 ที่มี class="special-title" = สีเขียว

#### 6.3 เปลี่ยนสี h1 เฉพาะ ID

```css
/* เปลี่ยนสี h1 ทั้งหมดเป็นสีม่วง */
h1 {
  color: purple;
}

/* เปลี่ยนสี h1 ที่มี class="special-title" เป็นสีส้ม */
h1.special-title {
  color: orange;
}

/* เปลี่ยนสี h1 ที่มี id="unique-title" เป็นสีชมพู */
#unique-title {
  color: hotpink;
}
```

**ผลลัพธ์:**

- h1 ปกติ = สีม่วง
- h1.special-title = สีส้ม
- #unique-title = สีชมพู (ID มี priority สูงสุด)

### ขั้นตอนที่ 7: ทดลองสีต่างๆ

```css
/* ทดลองสีแบบต่างๆ */

/* 1. สีชื่อ (Color Names) */
h1 {
  color: crimson; /* สีแดงเข้ม */
}

/* 2. สี Hex Code */
h1.special-title {
  color: #3498db; /* สีน้ำเงินสวย */
}

/* 3. สี RGB */
#unique-title {
  color: rgb(231, 76, 60); /* สีแดงส้ม */
}

/* 4. สี RGBA (มีความโปร่งใส) */
h2 {
  color: rgba(46, 204, 113, 0.8); /* สีเขียวโปร่งใส 80% */
}

/* 5. สี HSL */
.highlight {
  color: hsl(348, 83%, 47%); /* สีแดงในรูปแบบ HSL */
}
```

### ขั้นตอนที่ 8: เพิ่มสไตล์เสริม

```css
/* สไตล์เสริมสำหรับ h1 */
h1 {
  color: #2c3e50; /* สีน้ำเงินเข้ม */
  font-size: 2.5rem; /* ขนาดฟอนต์ */
  text-align: center; /* จัดกึ่งกลาง */
  margin-bottom: 1rem; /* ระยะห่างด้านล่าง */
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3); /* เงาข้อความ */
  transition: color 0.3s ease; /* เอฟเฟกต์เปลี่ยนสี */
}

/* เอฟเฟกต์เมื่อ hover */
h1:hover {
  color: #e74c3c; /* เปลี่ยนเป็นสีแดงเมื่อ hover */
  cursor: pointer; /* เปลี่ยน cursor */
}

/* สไตล์พิเศษสำหรับ class */
h1.special-title {
  color: #9b59b6; /* สีม่วง */
  font-style: italic; /* ตัวเอียง */
  text-decoration: underline; /* ขีดเส้นใต้ */
}

/* สไตล์พิเศษสำหรับ ID */
#unique-title {
  color: #f39c12; /* สีส้ม */
  background-color: #2c3e50; /* พื้นหลังสีเข้ม */
  padding: 1rem; /* เว้นพื้นที่ภายใน */
  border-radius: 10px; /* มุมโค้ง */
  color: white; /* ข้อความสีขาว */
}
```

## การตรวจสอบและแก้ปัญหา

### ปัญหาที่พบบ่อย

#### 1. ไฟล์ CSS ไม่ทำงาน

**สาเหตุที่เป็นไปได้:**

```html
<!-- ❌ ผิด: ลิงก์ไฟล์ CSS ไม่ถูกต้อง -->
<link rel="stylesheet" href="style.css" />
<!-- ชื่อไฟล์ผิด -->
<link rel="stylesheet" href="css/styles.css" />
<!-- path ผิด -->

<!-- ✅ ถูกต้อง -->
<link rel="stylesheet" href="styles.css" />
```

#### 2. โครงสร้างไฟล์ผิด

```
❌ ผิด:
project/
├── html/
│   └── index.html
└── css/
    └── styles.css

✅ ถูกต้อง:
project/
├── index.html
└── styles.css
```

#### 3. การเข้ารหัสภาษาไทย

```html
<!-- ❌ ไม่มี charset -->
<head>
  <title>เว็บไซต์ภาษาไทย</title>
</head>

<!-- ✅ มี charset -->
<head>
  <meta charset="UTF-8" />
  <title>เว็บไซต์ภาษาไทย</title>
</head>
```

### เครื่องมือตรวจสอบ

#### 1. Developer Tools

- กด **F12** หรือ **Ctrl+Shift+I**
- ดูแท็บ **Elements** เพื่อดูโครงสร้าง HTML
- ดูแท็บ **Console** เพื่อดู error

#### 2. ตรวจสอบการโหลดไฟล์

```html
<!-- ใน Developer Tools แท็บ Network -->
<!-- ดูว่าไฟล์ styles.css โหลดสำเร็จหรือไม่ -->
<!-- สถานะควรเป็น 200 (สำเร็จ) -->
```

## สรุปและแนวปฏิบัติที่ดี

### ✅ ควรทำ

1. **ตั้งชื่อไฟล์ให้ชัดเจน**

   ```
   index.html      (หน้าหลัก)
   styles.css      (CSS หลัก)
   main.css        (ทางเลือก)
   ```

2. **จัดโครงสร้างโฟลเดอร์**

   ```
   project/
   ├── index.html
   ├── styles.css
   ├── css/
   ├── images/
   └── js/
   ```

3. **ใส่ comments ใน CSS**

   ```css
   /* Header Styles */
   header {
     ...;
   }

   /* Navigation */
   nav {
     ...;
   }
   ```

4. **ใช้ path ที่ถูกต้อง**

   ```html
   <!-- ไฟล์เดียวกัน -->
   <link rel="stylesheet" href="styles.css" />

   <!-- ในโฟลเดอร์ย่อย -->
   <link rel="stylesheet" href="css/main.css" />
   ```

### ❌ ไม่ควรทำ

1. **ชื่อไฟล์ที่มีช่องว่าง**

   ```
   ❌ my styles.css
   ✅ my-styles.css หรือ myStyles.css
   ```

2. **ผสม HTML กับ CSS**

   ```html
   <!-- ❌ ไม่ดี -->
   <h1 style="color: red;">หัวข้อ</h1>

   <!-- ✅ ดี -->
   <h1 class="red-title">หัวข้อ</h1>
   ```

3. **ไม่มี backup**
   - สำรองไฟล์เป็นประจำ
   - ใช้ Version Control (Git)

การเริ่มต้นด้วยโครงสร้างที่ดีจะช่วยให้การพัฒนาเว็บไซต์เป็นไปอย่างราบรื่นและมีระเบียบ!
