# CSS คืออะไร: ความเป็นมาและหลักการแยกชั้น (Separation of Concerns)

## ความเป็นมาของ CSS (Cascading Style Sheets)

### ปัญหาในยุคแรกของเว็บ (1990s)

ในช่วงแรกของการพัฒนาเว็บไซต์ นักพัฒนาต้องใช้ HTML เพียงอย่างเดียวในการสร้างทั้งโครงสร้างและการจัดรูปแบบ ซึ่งทำให้เกิดปัญหาหลายประการ:

```html
<!-- ตัวอย่างการเขียน HTML แบบเก่า -->
<font color="red" size="5" face="Arial">
  <b><u>หัวข้อสำคัญ</u></b>
</font>
<br /><br />
<table bgcolor="yellow" border="1">
  <tr>
    <td><font color="blue">เนื้อหา</font></td>
  </tr>
</table>
```

**ปัญหาที่เกิดขึ้น:**

- โค้ดซับซ้อนและยากต่อการบำรุงรักษา
- การจัดรูปแบบและเนื้อหาปนกันอยู่ในไฟล์เดียว
- ต้องแก้ไขหลายจุดเมื่อต้องการเปลี่ยนสไตล์
- ไฟล์มีขนาดใหญ่และโหลดช้า

### การเกิดขึ้นของ CSS (1996)

CSS ถูกพัฒนาขึ้นโดย **Håkon Wium Lie** และ **Bert Bos** ที่ W3C เพื่อแก้ไขปัญหาเหล่านี้

## หลักการแยกชั้น (Separation of Concerns)

### 1. HTML: ชั้นโครงสร้าง (Structure Layer)

HTML รับผิดชอบในการกำหนด**โครงสร้างและความหมาย**ของเนื้อหา

```html
<!-- HTML เน้นความหมายและโครงสร้าง -->
<header>
  <h1>หัวข้อหลัก</h1>
  <nav>
    <ul>
      <li><a href="#home">หน้าแรก</a></li>
      <li><a href="#about">เกี่ยวกับ</a></li>
    </ul>
  </nav>
</header>

<main>
  <article>
    <h2>บทความ</h2>
    <p>เนื้อหาบทความ...</p>
  </article>
</main>
```

**หน้าที่ของ HTML:**

- กำหนดโครงสร้างเอกสาร (หัวข้อ, ย่อหน้า, รายการ)
- ให้ความหมายเชิงตรรกะ (semantic meaning)
- เป็นพื้นฐานที่เครื่องมือช่วยเหลือ (screen readers) ใช้อ่าน

### 2. CSS: ชั้นการนำเสนอ (Presentation Layer)

CSS รับผิดชอบในการกำหนด**รูปแบบและการจัดวาง**

```css
/* CSS เน้นการจัดรูปแบบ */
header {
  background-color: #2c3e50;
  color: white;
  padding: 1rem;
}

h1 {
  font-size: 2.5rem;
  margin: 0;
  text-align: center;
}

nav ul {
  display: flex;
  list-style: none;
  gap: 2rem;
}

nav a {
  color: white;
  text-decoration: none;
  transition: color 0.3s;
}

nav a:hover {
  color: #3498db;
}

main {
  max-width: 800px;
  margin: 2rem auto;
  padding: 0 1rem;
}
```

**หน้าที่ของ CSS:**

- กำหนดสี, ฟอนต์, ขนาด
- จัดวางตำแหน่งและเลย์เอาต์
- สร้างเอฟเฟกต์และ animation
- ทำให้เว็บไซต์ responsive

### 3. JavaScript: ชั้นพฤติกรรม (Behavior Layer)

JavaScript รับผิดชอบในการกำหนด**การโต้ตอบและพฤติกรรม**

```javascript
// JavaScript เน้นการโต้ตอบและพฤติกรรม
document.addEventListener('DOMContentLoaded', function () {
  // เพิ่มการโต้ตอบกับเมนู
  const navToggle = document.querySelector('.nav-toggle');
  const navMenu = document.querySelector('nav ul');

  navToggle.addEventListener('click', function () {
    navMenu.classList.toggle('active');
  });

  // เพิ่มเอฟเฟกต์ smooth scrolling
  document.querySelectorAll('a[href^="#"]').forEach((anchor) => {
    anchor.addEventListener('click', function (e) {
      e.preventDefault();
      const target = document.querySelector(this.getAttribute('href'));
      target.scrollIntoView({ behavior: 'smooth' });
    });
  });
});
```

**หน้าที่ของ JavaScript:**

- จัดการเหตุการณ์ (events)
- เปลี่ยนแปลงเนื้อหาแบบไดนามิก
- ตรวจสอบข้อมูล (validation)
- สื่อสารกับเซิร์ฟเวอร์ (AJAX)

## ประโยชน์ของการแยกชั้น

### 1. ความยืดหยุ่น (Flexibility)

```css
/* สามารถเปลี่ยนสไตล์ทั้งหมดโดยไม่แตะ HTML */
/* ธีมสีเข้ม */
body {
  background: #1a1a1a;
  color: #fff;
}

/* ธีมสีอ่อน */
body {
  background: #ffffff;
  color: #333;
}
```

### 2. การบำรุงรักษา (Maintainability)

- แก้ไขสไตล์ในที่เดียว ส่งผลกับทุกหน้า
- โค้ดอ่านง่ายและเข้าใจง่าย
- ทีมงานสามารถทำงานแยกส่วนได้

### 3. ประสิทธิภาพ (Performance)

- ไฟล์ CSS สามารถ cache ได้
- ลดขนาดไฟล์ HTML
- โหลดหน้าเว็บเร็วขึ้น

### 4. การเข้าถึง (Accessibility)

- HTML ที่สะอาดช่วยเครื่องมือช่วยเหลือ
- สามารถปิด CSS และยังอ่านเนื้อหาได้
- รองรับอุปกรณ์หลากหลายประเภท

## ตัวอย่างการเปรียบเทียบ

### แบบเก่า (ไม่แยกชั้น)

```html
<font color="red" size="5" face="Arial">
  <b>หัวข้อ</b>
</font>
<br /><br />
<font color="blue" size="3">เนื้อหา</font>
```

### แบบใหม่ (แยกชั้น)

```html
<!-- HTML: โครงสร้าง -->
<h1 class="main-title">หัวข้อ</h1>
<p class="content">เนื้อหา</p>
```

```css
/* CSS: การนำเสนอ */
.main-title {
  color: red;
  font-size: 2rem;
  font-family: Arial, sans-serif;
  font-weight: bold;
}

.content {
  color: blue;
  font-size: 1rem;
}
```

## สรุป

CSS เป็นการปฏิวัติในการพัฒนาเว็บไซต์ที่ช่วยแยก**การนำเสนอ**ออกจาก**โครงสร้าง** ทำให้:

- **HTML** = โครงสร้างและความหมาย
- **CSS** = รูปแบบและการจัดวาง
- **JavaScript** = การโต้ตอบและพฤติกรรม

การแยกชั้นนี้ทำให้การพัฒนาเว็บไซต์มีประสิทธิภาพ ยืดหยุ่น และบำรุงรักษาได้ง่ายขึ้น เป็นหลักการพื้นฐานที่สำคัญของการพัฒนาเว็บสมัยใหม่
