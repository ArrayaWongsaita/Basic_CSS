# CSS Attribute Selectors: [type], [type="email"], [href^="https"], [href$=".pdf"], [data-role*="card"]

## ภาพรวม CSS Attribute Selectors

CSS Attribute Selectors เป็นเครื่องมือที่ทรงพลังในการเลือก HTML elements ตาม attributes และค่าของ attributes โดยไม่ต้องพึ่งพา class หรือ id ทำให้สามารถสร้าง CSS ที่มีความยืดหยุ่นและสามารถปรับตัวได้

### รูปแบบ Attribute Selectors ทั้ง 7 แบบ:

1. **[attribute]** - มี attribute นี้
2. **[attribute="value"]** - มีค่าตรงกันแบบแน่นอน
3. **[attribute^="value"]** - เริ่มต้นด้วยค่านี้
4. **[attribute$="value"]** - ลงท้ายด้วยค่านี้
5. **[attribute*="value"]** - มีค่านี้อยู่ข้างใน
6. **[attribute~="value"]** - มีคำนี้ในรายการคำ
7. **[attribute|="value"]** - เริ่มต้นด้วยคำนี้หรือตามด้วย hyphen

## 1. Basic Attribute Selector [attribute]

### ความหมาย

เลือก elements ที่มี attribute นั้นๆ อยู่ ไม่ว่าจะมีค่าอะไร

### รูปแบบ

```css
[attribute] {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### Form Elements

```html
<!-- HTML -->
<form>
  <input type="text" placeholder="ชื่อ" />
  <input type="email" placeholder="อีเมล" required />
  <input type="password" placeholder="รหัสผ่าน" required />
  <textarea placeholder="ข้อความ"></textarea>
  <button type="submit">ส่ง</button>
</form>
```

```css
/* เลือก input ทั้งหมดที่มี attribute required */
[required] {
  border: 2px solid #e74c3c;
  border-left: 4px solid #c0392b;
}

/* เลือก elements ทั้งหมดที่มี placeholder */
[placeholder] {
  font-style: italic;
  color: #7f8c8d;
}

[placeholder]:focus {
  font-style: normal;
}

/* เลือก input ที่มี type attribute */
[type] {
  padding: 0.75rem;
  border-radius: 4px;
  border: 1px solid #bdc3c7;
  font-size: 1rem;
}
```

#### Links และ Media

```html
<!-- HTML -->
<div class="content">
  <a href="https://example.com">External Link</a>
  <a href="#section1">Internal Link</a>
  <a href="mailto:test@example.com">Email Link</a>
  <img src="image.jpg" alt="Description" />
  <img src="logo.png" />
  <video controls>
    <source src="video.mp4" type="video/mp4" />
  </video>
</div>
```

```css
/* เลือก links ที่มี href */
[href] {
  color: #3498db;
  text-decoration: none;
  transition: color 0.3s;
}

[href]:hover {
  color: #2980b9;
  text-decoration: underline;
}

/* เลือก images ที่มี alt attribute */
[alt] {
  border: 2px solid #2ecc71;
  padding: 4px;
}

/* เลือก media elements ที่มี controls */
[controls] {
  width: 100%;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
```

#### Custom Data Attributes

```html
<!-- HTML -->
<div data-role="card" data-status="active">การ์ดที่ 1</div>
<div data-role="card" data-status="inactive">การ์ดที่ 2</div>
<div data-component="modal">Modal</div>
<div data-track="analytics">Tracked Element</div>
```

```css
/* เลือก elements ที่มี data-role */
[data-role] {
  padding: 1rem;
  border-radius: 6px;
  margin-bottom: 1rem;
}

/* เลือก elements ที่มี data-status */
[data-status] {
  position: relative;
}

[data-status]::before {
  content: '';
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: #95a5a6;
}

/* เลือก elements ที่มี data-track */
[data-track] {
  cursor: pointer;
  transition: transform 0.2s;
}

[data-track]:hover {
  transform: scale(1.02);
}
```

## 2. Exact Match Selector [attribute="value"]

### ความหมาย

เลือก elements ที่มี attribute และค่าตรงกันแบบแน่นอน

### รูปแบบ

```css
[attribute='value'] {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### Input Types

```html
<!-- HTML -->
<form class="contact-form">
  <input type="text" placeholder="ชื่อ" />
  <input type="email" placeholder="อีเมล" />
  <input type="password" placeholder="รหัสผ่าน" />
  <input type="tel" placeholder="เบอร์โทร" />
  <input type="url" placeholder="เว็บไซต์" />
  <input type="number" placeholder="อายุ" />
  <input type="submit" value="ส่งข้อมูล" />
  <input type="reset" value="ล้างข้อมูล" />
</form>
```

```css
/* Text inputs */
[type='text'],
[type='email'],
[type='password'],
[type='tel'],
[type='url'] {
  width: 100%;
  padding: 0.75rem;
  margin-bottom: 1rem;
  border: 1px solid #bdc3c7;
  border-radius: 4px;
  font-size: 1rem;
  transition: border-color 0.3s;
}

[type='text']:focus,
[type='email']:focus,
[type='password']:focus,
[type='tel']:focus,
[type='url']:focus {
  border-color: #3498db;
  outline: none;
  box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
}

/* Email input specific styling */
[type='email'] {
  background-image: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path fill="%23999" d="M2.003 5.884L10 9.882l7.997-3.998A2 2 0 0016 4H4a2 2 0 00-1.997 1.884z"/><path fill="%23999" d="M18 8.118l-8 4-8-4V14a2 2 0 002 2h12a2 2 0 002-2V8.118z"/></svg>');
  background-repeat: no-repeat;
  background-position: right 0.75rem center;
  background-size: 1rem;
  padding-right: 2.5rem;
}

/* Number input */
[type='number'] {
  width: 30%;
  padding: 0.75rem;
  border: 1px solid #bdc3c7;
  border-radius: 4px;
}

/* Submit button */
[type='submit'] {
  background: #2ecc71;
  color: white;
  border: none;
  padding: 0.75rem 2rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  margin-right: 0.5rem;
  transition: background-color 0.3s;
}

[type='submit']:hover {
  background: #27ae60;
}

/* Reset button */
[type='reset'] {
  background: #95a5a6;
  color: white;
  border: none;
  padding: 0.75rem 2rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s;
}

[type='reset']:hover {
  background: #7f8c8d;
}
```

#### Link Types

```html
<!-- HTML -->
<nav class="navigation">
  <a href="index.html" rel="home">หน้าแรก</a>
  <a href="about.html" rel="about">เกี่ยวกับ</a>
  <a href="contact.html" rel="contact">ติดต่อ</a>
  <a href="https://facebook.com" rel="external">Facebook</a>
  <a href="https://twitter.com" rel="external">Twitter</a>
  <a href="#" rel="nofollow">No Follow Link</a>
</nav>
```

```css
/* External links */
[rel='external'] {
  color: #e67e22;
  font-weight: 600;
}

[rel='external']::after {
  content: ' ↗';
  font-size: 0.8em;
  vertical-align: super;
}

/* No follow links */
[rel='nofollow'] {
  color: #95a5a6;
  text-decoration: line-through;
}

/* Home link */
[rel='home'] {
  font-weight: bold;
  color: #2c3e50;
}
```

#### Custom Attributes

```html
<!-- HTML -->
<div class="dashboard">
  <div data-status="active" data-priority="high">Task 1</div>
  <div data-status="pending" data-priority="medium">Task 2</div>
  <div data-status="completed" data-priority="low">Task 3</div>
  <div data-status="cancelled" data-priority="high">Task 4</div>
</div>
```

```css
/* Status styling */
[data-status='active'] {
  background: #d5f4e6;
  border-left: 4px solid #2ecc71;
  color: #27ae60;
}

[data-status='pending'] {
  background: #fef9e7;
  border-left: 4px solid #f39c12;
  color: #e67e22;
}

[data-status='completed'] {
  background: #eaf2f8;
  border-left: 4px solid #3498db;
  color: #2980b9;
}

[data-status='cancelled'] {
  background: #fadbd8;
  border-left: 4px solid #e74c3c;
  color: #c0392b;
}

/* Priority styling */
[data-priority='high'] {
  font-weight: bold;
  box-shadow: 0 2px 8px rgba(231, 76, 60, 0.2);
}

[data-priority='medium'] {
  font-weight: 500;
}

[data-priority='low'] {
  opacity: 0.8;
}
```

## 3. Starts With Selector [attribute^="value"]

### ความหมาย

เลือก elements ที่มี attribute เริ่มต้นด้วยค่าที่กำหนด

### รูปแบบ

```css
[attribute^='value'] {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### External Links

```html
<!-- HTML -->
<div class="links">
  <a href="https://google.com">Google</a>
  <a href="https://facebook.com">Facebook</a>
  <a href="http://oldsite.com">Old Site</a>
  <a href="mailto:test@example.com">Email</a>
  <a href="tel:+66812345678">Phone</a>
  <a href="#section1">Internal Link</a>
  <a href="page.html">Local Page</a>
</div>
```

```css
/* HTTPS links */
[href^='https'] {
  color: #27ae60;
  font-weight: 600;
}

[href^='https']::before {
  content: '🔒 ';
  color: #2ecc71;
}

/* HTTP links (insecure) */
[href^="http://"]
{
  color: #e67e22;
  text-decoration: underline wavy;
}

[href^="http://"]::before
{
  content: '⚠️ ';
}

/* Email links */
[href^='mailto'] {
  color: #3498db;
  font-style: italic;
}

[href^='mailto']::before {
  content: '✉️ ';
}

/* Phone links */
[href^='tel'] {
  color: #9b59b6;
  font-weight: 600;
}

[href^='tel']::before {
  content: '📞 ';
}
```

#### File Types by URL

```html
<!-- HTML -->
<div class="downloads">
  <a href="/downloads/manual.pdf">คู่มือการใช้งาน</a>
  <a href="/images/photo.jpg">รูปภาพ</a>
  <a href="/documents/report.docx">รายงาน</a>
  <a href="/videos/tutorial.mp4">วิดีโอสอน</a>
  <a href="/archives/backup.zip">ไฟล์สำรอง</a>
</div>
```

```css
/* PDF files */
[href^='/downloads'] {
  color: #e74c3c;
  font-weight: 600;
}

[href^='/downloads']::after {
  content: ' [PDF]';
  font-size: 0.8em;
  color: #c0392b;
  font-weight: normal;
}

/* Images */
[href^='/images'] {
  color: #f39c12;
}

[href^='/images']::after {
  content: ' [IMG]';
  font-size: 0.8em;
  color: #e67e22;
}

/* Documents */
[href^='/documents'] {
  color: #3498db;
}

[href^='/documents']::after {
  content: ' [DOC]';
  font-size: 0.8em;
  color: #2980b9;
}

/* Videos */
[href^='/videos'] {
  color: #9b59b6;
}

[href^='/videos']::after {
  content: ' [VIDEO]';
  font-size: 0.8em;
  color: #8e44ad;
}
```

#### Class Prefix Patterns

```html
<!-- HTML -->
<div class="ui-components">
  <button class="btn-primary">Primary</button>
  <button class="btn-secondary">Secondary</button>
  <button class="btn-danger">Danger</button>
  <div class="icon-home">Home Icon</div>
  <div class="icon-user">User Icon</div>
  <div class="icon-settings">Settings Icon</div>
</div>
```

```css
/* Button classes starting with "btn-" */
[class^='btn-'] {
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  transition: all 0.3s;
  margin-right: 0.5rem;
}

/* Icon classes starting with "icon-" */
[class^='icon-'] {
  display: inline-block;
  padding: 0.5rem;
  margin-right: 0.5rem;
  border-radius: 4px;
  background: #ecf0f1;
  font-size: 0.9rem;
}

[class^='icon-']::before {
  content: '🔸 ';
  margin-right: 0.25rem;
}
```

## 4. Ends With Selector [attribute$="value"]

### ความหมาย

เลือก elements ที่มี attribute ลงท้ายด้วยค่าที่กำหนด

### รูปแบบ

```css
[attribute$='value'] {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### File Extensions

```html
<!-- HTML -->
<div class="file-list">
  <a href="document.pdf">คู่มือการใช้งาน</a>
  <a href="spreadsheet.xlsx">ตารางคำนวณ</a>
  <a href="presentation.pptx">การนำเสนอ</a>
  <a href="image.jpg">รูปภาพ</a>
  <a href="photo.png">รูปถ่าย</a>
  <a href="video.mp4">วิดีโอ</a>
  <a href="audio.mp3">เสียง</a>
  <a href="archive.zip">ไฟล์บีบอัด</a>
  <a href="webpage.html">หน้าเว็บ</a>
</div>
```

```css
/* PDF files */
[href$='.pdf'] {
  color: #e74c3c;
  font-weight: 600;
}

[href$='.pdf']::before {
  content: '📄 ';
}

[href$='.pdf']::after {
  content: ' (PDF)';
  font-size: 0.8em;
  color: #c0392b;
}

/* Excel files */
[href$='.xlsx'],
[href$='.xls'] {
  color: #27ae60;
  font-weight: 600;
}

[href$='.xlsx']::before,
[href$='.xls']::before {
  content: '📊 ';
}

/* PowerPoint files */
[href$='.pptx'],
[href$='.ppt'] {
  color: #e67e22;
  font-weight: 600;
}

[href$='.pptx']::before,
[href$='.ppt']::before {
  content: '📋 ';
}

/* Image files */
[href$='.jpg'],
[href$='.jpeg'],
[href$='.png'],
[href$='.gif'],
[href$='.webp'] {
  color: #f39c12;
  font-weight: 500;
}

[href$='.jpg']::before,
[href$='.jpeg']::before,
[href$='.png']::before,
[href$='.gif']::before,
[href$='.webp']::before {
  content: '🖼️ ';
}

/* Video files */
[href$='.mp4'],
[href$='.avi'],
[href$='.mov'],
[href$='.wmv'] {
  color: #9b59b6;
  font-weight: 600;
}

[href$='.mp4']::before,
[href$='.avi']::before,
[href$='.mov']::before,
[href$='.wmv']::before {
  content: '🎥 ';
}

/* Audio files */
[href$='.mp3'],
[href$='.wav'],
[href$='.ogg'] {
  color: #1abc9c;
  font-weight: 500;
}

[href$='.mp3']::before,
[href$='.wav']::before,
[href$='.ogg']::before {
  content: '🎵 ';
}

/* Archive files */
[href$='.zip'],
[href$='.rar'],
[href$='.7z'] {
  color: #34495e;
  font-weight: 600;
}

[href$='.zip']::before,
[href$='.rar']::before,
[href$='.7z']::before {
  content: '📦 ';
}

/* HTML files */
[href$='.html'],
[href$='.htm'] {
  color: #3498db;
}

[href$='.html']::before,
[href$='.htm']::before {
  content: '🌐 ';
}
```

#### Email Domains

```html
<!-- HTML -->
<div class="contacts">
  <a href="mailto:user@gmail.com">Gmail User</a>
  <a href="mailto:contact@yahoo.com">Yahoo Contact</a>
  <a href="mailto:support@company.co.th">Local Company</a>
  <a href="mailto:admin@government.go.th">Government</a>
  <a href="mailto:info@university.ac.th">University</a>
</div>
```

```css
/* Gmail addresses */
[href$='@gmail.com'] {
  color: #ea4335;
  font-weight: 600;
}

[href$='@gmail.com']::before {
  content: 'Gmail: ';
  font-size: 0.8em;
  text-transform: uppercase;
}

/* Yahoo addresses */
[href$='@yahoo.com'] {
  color: #7b0099;
  font-weight: 600;
}

/* Thai domains */
[href$='.co.th'],
[href$='.go.th'],
[href$='.ac.th'] {
  background: linear-gradient(45deg, #ff0000, #ffffff, #0000ff);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  font-weight: bold;
}

[href$='.co.th']::after {
  content: ' 🇹🇭';
}

[href$='.go.th']::after {
  content: ' 🏛️';
}

[href$='.ac.th']::after {
  content: ' 🎓';
}
```

## 5. Contains Selector [attribute*="value"]

### ความหมาย

เลือก elements ที่มี attribute ที่มีค่าที่กำหนดอยู่ข้างในไม่ว่าจะอยู่ตำแหน่งไหน

### รูปแบบ

```css
[attribute*='value'] {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### Data Attributes with Keywords

```html
<!-- HTML -->
<div class="products">
  <div data-role="product-card" data-category="electronics">โทรศัพท์</div>
  <div data-role="product-card" data-category="clothing">เสื้อผ้า</div>
  <div data-role="sidebar-card" data-category="electronics">แล็ปท็อป</div>
  <div data-role="hero-card" data-category="books">หนังสือ</div>
  <div data-role="product-list" data-category="electronics">รายการสินค้า</div>
</div>
```

```css
/* Elements with "card" in data-role */
[data-role*='card'] {
  background: white;
  border: 1px solid #dee2e6;
  border-radius: 8px;
  padding: 1.5rem;
  margin-bottom: 1rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s, box-shadow 0.2s;
}

[data-role*='card']:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

/* Elements with "product" in data-role */
[data-role*='product'] {
  border-left: 4px solid #3498db;
}

/* Elements with "electronics" in data-category */
[data-category*='electronics'] {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

/* Elements with "clothing" in data-category */
[data-category*='clothing'] {
  background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
  color: white;
}

/* Elements with "books" in data-category */
[data-category*='books'] {
  background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
  color: white;
}
```

#### Class Names with Keywords

```html
<!-- HTML -->
<div class="components">
  <div class="btn btn-primary btn-large">Large Primary Button</div>
  <div class="btn btn-secondary btn-small">Small Secondary Button</div>
  <div class="card card-primary card-shadow">Primary Card</div>
  <div class="card card-secondary">Secondary Card</div>
  <div class="alert alert-success alert-dismissible">Success Alert</div>
  <div class="alert alert-danger">Danger Alert</div>
</div>
```

```css
/* Elements with "btn" in class */
[class*='btn'] {
  display: inline-block;
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  text-decoration: none;
  transition: all 0.3s;
  margin: 0.25rem;
}

/* Elements with "primary" in class */
[class*='primary'] {
  background: #007bff;
  color: white;
}

[class*='primary']:hover {
  background: #0056b3;
}

/* Elements with "secondary" in class */
[class*='secondary'] {
  background: #6c757d;
  color: white;
}

[class*='secondary']:hover {
  background: #545b62;
}

/* Elements with "large" in class */
[class*='large'] {
  font-size: 1.25rem;
  padding: 1rem 2rem;
}

/* Elements with "small" in class */
[class*='small'] {
  font-size: 0.875rem;
  padding: 0.5rem 1rem;
}

/* Elements with "shadow" in class */
[class*='shadow'] {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

/* Elements with "alert" in class */
[class*='alert'] {
  padding: 1rem;
  border-radius: 4px;
  margin-bottom: 1rem;
  border: 1px solid transparent;
}

[class*='success'] {
  background: #d4edda;
  border-color: #c3e6cb;
  color: #155724;
}

[class*='danger'] {
  background: #f8d7da;
  border-color: #f5c6cb;
  color: #721c24;
}

/* Elements with "dismissible" in class */
[class*='dismissible'] {
  position: relative;
  padding-right: 3rem;
}

[class*='dismissible']::after {
  content: '✕';
  position: absolute;
  top: 1rem;
  right: 1rem;
  cursor: pointer;
  color: inherit;
  opacity: 0.7;
}
```

#### URL Patterns

```html
<!-- HTML -->
<div class="navigation">
  <a href="/admin/dashboard">Dashboard</a>
  <a href="/admin/users">Users</a>
  <a href="/api/v1/products">API Products</a>
  <a href="/api/v2/orders">API Orders</a>
  <a href="/public/downloads/manual.pdf">Public Manual</a>
  <a href="/private/documents/report.pdf">Private Report</a>
</div>
```

```css
/* Links containing "admin" in href */
[href*='admin'] {
  background: #e74c3c;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  text-decoration: none;
  margin: 0.25rem;
  display: inline-block;
}

[href*='admin']::before {
  content: '🔐 Admin: ';
}

/* Links containing "api" in href */
[href*='api'] {
  background: #f39c12;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  text-decoration: none;
  margin: 0.25rem;
  display: inline-block;
  font-family: monospace;
}

[href*='api']::before {
  content: '🔗 API: ';
}

/* Links containing "public" in href */
[href*='public'] {
  background: #27ae60;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  text-decoration: none;
  margin: 0.25rem;
  display: inline-block;
}

[href*='public']::before {
  content: '🌐 Public: ';
}

/* Links containing "private" in href */
[href*='private'] {
  background: #8e44ad;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  text-decoration: none;
  margin: 0.25rem;
  display: inline-block;
}

[href*='private']::before {
  content: '🔒 Private: ';
}
```

## 6. Word Match Selector [attribute~="value"]

### ความหมาย

เลือก elements ที่มี attribute ซึ่งมีคำที่กำหนดเป็นหนึ่งในรายการคำที่คั่นด้วยช่องว่าง

### รูปแบบ

```css
[attribute~='value'] {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### Class Lists

```html
<!-- HTML -->
<div class="components">
  <div class="btn primary large">Button 1</div>
  <div class="btn secondary small">Button 2</div>
  <div class="card primary shadow">Card 1</div>
  <div class="card secondary">Card 2</div>
  <div class="alert success dismissible">Alert 1</div>
  <div class="alert danger">Alert 2</div>
</div>
```

```css
/* Elements with "primary" as a complete word in class */
[class~='primary'] {
  background: #007bff;
  color: white;
}

/* Elements with "secondary" as a complete word in class */
[class~='secondary'] {
  background: #6c757d;
  color: white;
}

/* Elements with "large" as a complete word in class */
[class~='large'] {
  font-size: 1.25rem;
  padding: 1rem 2rem;
}

/* Elements with "small" as a complete word in class */
[class~='small'] {
  font-size: 0.875rem;
  padding: 0.5rem 1rem;
}

/* Elements with "shadow" as a complete word in class */
[class~='shadow'] {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}
```

#### Data Attributes with Multiple Values

```html
<!-- HTML -->
<div class="products">
  <div data-tags="electronics mobile smartphone">iPhone</div>
  <div data-tags="electronics computer laptop">MacBook</div>
  <div data-tags="clothing fashion shirt">เสื้อเชิ้ต</div>
  <div data-tags="books education programming">หนังสือโปรแกรม</div>
  <div data-tags="electronics mobile tablet">iPad</div>
</div>
```

```css
/* Products tagged with "electronics" */
[data-tags~='electronics'] {
  border-left: 4px solid #3498db;
  background: #ebf5ff;
}

/* Products tagged with "mobile" */
[data-tags~='mobile'] {
  position: relative;
}

[data-tags~='mobile']::after {
  content: '📱';
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
}

/* Products tagged with "clothing" */
[data-tags~='clothing'] {
  border-left: 4px solid #e91e63;
  background: #fce4ec;
}

/* Products tagged with "books" */
[data-tags~='books'] {
  border-left: 4px solid #ff9800;
  background: #fff3e0;
}

/* Products tagged with "laptop" */
[data-tags~='laptop']::after {
  content: '💻';
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
}

/* Products tagged with "smartphone" */
[data-tags~='smartphone']::before {
  content: 'Smart ';
  font-weight: bold;
  color: #2196f3;
}
```

## 7. Language/Prefix Match Selector [attribute|="value"]

### ความหมาย

เลือก elements ที่มี attribute เริ่มต้นด้วยค่าที่กำหนด ตามด้วย hyphen (-) หรือเป็นค่าเดียวกันแบบแน่นอน

### รูปแบบ

```css
[attribute|='value'] {
  property: value;
}
```

### ตัวอย่างการใช้งาน

#### Language Attributes

```html
<!-- HTML -->
<div class="content">
  <p lang="th">เนื้อหาภาษาไทย</p>
  <p lang="th-TH">เนื้อหาภาษาไทย (ประเทศไทย)</p>
  <p lang="en">English content</p>
  <p lang="en-US">American English content</p>
  <p lang="en-GB">British English content</p>
  <p lang="zh">中文内容</p>
  <p lang="zh-CN">简体中文内容</p>
  <p lang="zh-TW">繁體中文內容</p>
</div>
```

```css
/* Thai language content */
[lang|='th'] {
  font-family: 'Sarabun', 'Kanit', sans-serif;
  line-height: 1.8;
  color: #2c3e50;
}

/* English language content */
[lang|='en'] {
  font-family: 'Roboto', 'Arial', sans-serif;
  line-height: 1.6;
  color: #34495e;
}

/* Chinese language content */
[lang|='zh'] {
  font-family: 'Noto Sans CJK SC', '微软雅黑', sans-serif;
  line-height: 1.7;
  color: #2c3e50;
}

/* Specific language variants */
[lang='en-US'] {
  border-left: 3px solid #ff0000;
  padding-left: 1rem;
}

[lang='en-GB'] {
  border-left: 3px solid #0000ff;
  padding-left: 1rem;
}

[lang='zh-CN'] {
  border-left: 3px solid #ff0000;
  padding-left: 1rem;
}

[lang='zh-TW'] {
  border-left: 3px solid #0000ff;
  padding-left: 1rem;
}
```

#### Version Prefixes

```html
<!-- HTML -->
<div class="api-docs">
  <div data-version="v1">API Version 1.0</div>
  <div data-version="v1-beta">API Version 1.0 Beta</div>
  <div data-version="v1-alpha">API Version 1.0 Alpha</div>
  <div data-version="v2">API Version 2.0</div>
  <div data-version="v2-beta">API Version 2.0 Beta</div>
  <div data-version="v3">API Version 3.0</div>
</div>
```

```css
/* Version 1.x APIs */
[data-version|='v1'] {
  background: #f8f9fa;
  border: 1px solid #e9ecef;
  color: #6c757d;
}

[data-version|='v1']::before {
  content: 'Legacy: ';
  font-weight: bold;
  color: #dc3545;
}

/* Version 2.x APIs */
[data-version|='v2'] {
  background: #e3f2fd;
  border: 1px solid #2196f3;
  color: #1976d2;
}

[data-version|='v2']::before {
  content: 'Stable: ';
  font-weight: bold;
  color: #2196f3;
}

/* Version 3.x APIs */
[data-version|='v3'] {
  background: #e8f5e8;
  border: 1px solid #4caf50;
  color: #388e3c;
}

[data-version|='v3']::before {
  content: 'Latest: ';
  font-weight: bold;
  color: #4caf50;
}
```

## การรวม Attribute Selectors

### Multiple Attributes

```html
<!-- HTML -->
<form class="registration">
  <input type="email" required placeholder="อีเมล" />
  <input type="password" required placeholder="รหัสผ่าน" />
  <input type="text" placeholder="ชื่อ (ไม่จำเป็น)" />
  <input type="submit" value="สมัครสมาชิก" />
</form>
```

```css
/* Required email input */
[type='email'][required] {
  border: 2px solid #e74c3c;
  background: #fff5f5;
}

[type='email'][required]:valid {
  border-color: #27ae60;
  background: #f8fff8;
}

/* Required password input */
[type='password'][required] {
  border: 2px solid #e74c3c;
}

[type='password'][required]:valid {
  border-color: #27ae60;
}

/* All required inputs with placeholder */
[required][placeholder] {
  position: relative;
}

[required][placeholder]::after {
  content: ' *';
  color: #e74c3c;
  font-weight: bold;
}
```

### Complex Combinations

```html
<!-- HTML -->
<div class="media-gallery">
  <a href="image1.jpg" data-lightbox="gallery" title="รูปที่ 1">
    <img src="thumb1.jpg" alt="Thumbnail 1" />
  </a>
  <a href="image2.png" data-lightbox="gallery" title="รูปที่ 2">
    <img src="thumb2.jpg" alt="Thumbnail 2" />
  </a>
  <a href="video.mp4" data-lightbox="video" title="วิดีโอ">
    <img src="video-thumb.jpg" alt="Video Thumbnail" />
  </a>
</div>
```

```css
/* Image links in lightbox gallery */
[href$='.jpg'][data-lightbox='gallery'],
[href$='.png'][data-lightbox='gallery'],
[href$='.gif'][data-lightbox='gallery'] {
  display: inline-block;
  border: 3px solid #3498db;
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.3s;
}

[href$='.jpg'][data-lightbox='gallery']:hover,
[href$='.png'][data-lightbox='gallery']:hover,
[href$='.gif'][data-lightbox='gallery']:hover {
  transform: scale(1.05);
}

/* Video links */
[href$='.mp4'][data-lightbox] {
  position: relative;
  display: inline-block;
}

[href$='.mp4'][data-lightbox]::before {
  content: '▶️';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 2rem;
  color: white;
  background: rgba(0, 0, 0, 0.7);
  padding: 0.5rem;
  border-radius: 50%;
  z-index: 1;
}

/* Elements with title attribute */
[title] {
  cursor: help;
}

[title]:hover::after {
  content: attr(title);
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  background: #333;
  color: white;
  padding: 0.5rem;
  border-radius: 4px;
  font-size: 0.875rem;
  white-space: nowrap;
  z-index: 1000;
}
```

## Performance และ Best Practices

### ข้อควรระวังเรื่อง Performance

```css
/* ❌ ช้า: Attribute selectors ที่ซับซ้อน */
div[class*='component'] span[data-role*='button'] a[href^='https'] {
  color: red;
}

/* ✅ เร็วกว่า: ใช้ class เฉพาะ */
.external-link-button {
  color: red;
}

/* ❌ ช้า: Universal selector กับ attribute */
*[data-track] {
  cursor: pointer;
}

/* ✅ เร็วกว่า: Element specific */
a[data-track],
button[data-track] {
  cursor: pointer;
}
```

### Best Practices

```css
/* ✅ ดี: ใช้สำหรับ progressive enhancement */
[hidden] {
  display: none;
}

[disabled] {
  opacity: 0.6;
  cursor: not-allowed;
}

/* ✅ ดี: ใช้กับ semantic attributes */
[aria-expanded='true'] + .dropdown-menu {
  display: block;
}

[aria-current='page'] {
  font-weight: bold;
  color: #007bff;
}

/* ✅ ดี: ใช้กับ data attributes สำหรับ state */
[data-state='loading']::after {
  content: '⏳ Loading...';
}

[data-state='error'] {
  color: #dc3545;
  border-color: #dc3545;
}

[data-state='success'] {
  color: #28a745;
  border-color: #28a745;
}
```

## สรุป

### Attribute Selectors ทั้ง 7 แบบ:

1. **[attribute]** - มี attribute
2. **[attribute="value"]** - ค่าตรงแน่นอน
3. **[attribute^="value"]** - เริ่มต้นด้วย
4. **[attribute$="value"]** - ลงท้ายด้วย
5. **[attribute*="value"]** - มีอยู่ข้างใน
6. **[attribute~="value"]** - คำในรายการ
7. **[attribute|="value"]** - คำหรือ prefix

### การใช้งานที่เหมาะสม:

- **File types**: `[href$=".pdf"]`
- **External links**: `[href^="https"]`
- **Form validation**: `[type="email"][required]`
- **Data attributes**: `[data-role*="card"]`
- **Language**: `[lang|="th"]`
- **Progressive enhancement**: `[hidden]`, `[disabled]`

### ข้อดี:

- ไม่ต้องเพิ่ม class/id
- เหมาะสำหรับ semantic HTML
- Progressive enhancement
- Dynamic content

### ข้อควรระวัง:

- Performance ช้ากว่า class/id selectors
- Browser support (เก่าอาจไม่รองรับ)
- ความซับซ้อนในการ debug

การใช้ Attribute Selectors อย่างชาญฉลาดจะช่วยให้ CSS มีความยืดหยุ่นและสามารถจัดการกับเนื้อหาที่เปลี่ยนแปลงได้ดีขึ้น!
