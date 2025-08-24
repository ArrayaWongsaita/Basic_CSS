# CSS Pseudo-classes พื้นฐาน: :hover, :active, :focus, :visited, :checked และอื่นๆ

## ภาพรวม CSS Pseudo-classes

CSS Pseudo-classes เป็น selectors พิเศษที่ใช้เลือก elements ตามสถานะ (state) หรือตำแหน่ง (position) ใน DOM tree โดยไม่ต้องเพิ่ม class หรือ attribute ใน HTML ทำให้สามารถสร้าง interactive UI และ responsive design ได้อย่างมีประสิทธิภาพ

### รูปแบบพื้นฐาน

```css
selector:pseudo-class {
  property: value;
}
```

### หมวดหมู่ของ Pseudo-classes

1. **Interactive States** - :hover, :active, :focus, :focus-visible
2. **Link States** - :visited, :link
3. **Form States** - :checked, :disabled, :required, :valid, :invalid
4. **Structural** - :nth-child(), :nth-of-type(), :first-child, :last-child
5. **Logical** - :not(), :is(), :where()

## 1. Interactive States Pseudo-classes

### 1.1 :hover - เมื่อเมาส์วางบน Element

#### ความหมาย

`:hover` ใช้เลือก element เมื่อผู้ใช้วางเมาส์เหนือ element นั้น

#### ตัวอย่างการใช้งาน

##### Button Hover Effects

```html
<!-- HTML -->
<div class="button-examples">
  <button class="btn-basic">Basic Button</button>
  <button class="btn-gradient">Gradient Button</button>
  <button class="btn-scale">Scale Button</button>
  <button class="btn-slide">Slide Effect</button>
</div>
```

```css
/* Basic hover effect */
.btn-basic {
  background: #3498db;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn-basic:hover {
  background: #2980b9;
}

/* Gradient hover effect */
.btn-gradient {
  background: linear-gradient(45deg, #667eea, #764ba2);
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-gradient:hover {
  background: linear-gradient(45deg, #764ba2, #667eea);
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

/* Scale hover effect */
.btn-scale {
  background: #e74c3c;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  transition: transform 0.2s ease;
}

.btn-scale:hover {
  transform: scale(1.05);
}

/* Slide effect */
.btn-slide {
  background: #2ecc71;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  position: relative;
  overflow: hidden;
  transition: color 0.3s ease;
}

.btn-slide::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: #27ae60;
  transition: left 0.3s ease;
  z-index: -1;
}

.btn-slide:hover::before {
  left: 0;
}
```

##### Card Hover Effects

```html
<!-- HTML -->
<div class="card-grid">
  <div class="card">
    <img src="image1.jpg" alt="Card Image" />
    <div class="card-content">
      <h3>Card Title</h3>
      <p>Card description text...</p>
      <a href="#" class="card-link">Read More</a>
    </div>
  </div>
</div>
```

```css
.card {
  background: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
}

.card:hover {
  transform: translateY(-8px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.card img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.card:hover img {
  transform: scale(1.1);
}

.card-content {
  padding: 1.5rem;
}

.card-link {
  color: #3498db;
  text-decoration: none;
  font-weight: 600;
  transition: color 0.3s ease;
}

.card:hover .card-link {
  color: #2980b9;
}
```

##### Navigation Hover Effects

```html
<!-- HTML -->
<nav class="main-nav">
  <ul>
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
```

```css
.main-nav ul {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  background: #2c3e50;
}

.main-nav li {
  position: relative;
}

.main-nav a {
  display: block;
  color: white;
  text-decoration: none;
  padding: 1rem 1.5rem;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.main-nav a::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 3px;
  background: #3498db;
  transition: width 0.3s ease;
}

.main-nav a:hover {
  background: #34495e;
  color: #3498db;
}

.main-nav a:hover::before {
  width: 100%;
}
```

### 1.2 :active - เมื่อคลิกหรือกดบน Element

#### ความหมาย

`:active` ใช้เลือก element ขณะที่ผู้ใช้กำลังคลิกหรือกดอยู่

#### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<div class="interactive-buttons">
  <button class="btn-press">Press Effect</button>
  <button class="btn-ripple">Ripple Effect</button>
  <a href="#" class="link-active">Active Link</a>
</div>
```

```css
/* Press down effect */
.btn-press {
  background: #3498db;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.1s ease;
  transform: translateY(0);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.btn-press:active {
  transform: translateY(2px);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

/* Ripple effect simulation */
.btn-ripple {
  background: #e74c3c;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.btn-ripple:active {
  background: #c0392b;
}

.btn-ripple:active::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.5);
  transform: translate(-50%, -50%);
  animation: ripple 0.6s ease-out;
}

@keyframes ripple {
  to {
    width: 300px;
    height: 300px;
    opacity: 0;
  }
}

/* Active link state */
.link-active {
  color: #3498db;
  text-decoration: none;
  padding: 0.5rem;
  border-radius: 4px;
  transition: all 0.2s ease;
}

.link-active:active {
  background: #3498db;
  color: white;
  transform: scale(0.95);
}
```

### 1.3 :focus - เมื่อ Element ได้รับ Focus

#### ความหมาย

`:focus` ใช้เลือก element ที่กำลังได้รับ focus (เช่น การกด Tab หรือคลิกใน input field)

#### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<form class="focus-form">
  <div class="form-group">
    <label for="name">ชื่อ:</label>
    <input type="text" id="name" name="name" placeholder="กรอกชื่อของคุณ" />
  </div>

  <div class="form-group">
    <label for="email">อีเมล:</label>
    <input type="email" id="email" name="email" placeholder="กรอกอีเมลของคุณ" />
  </div>

  <div class="form-group">
    <label for="message">ข้อความ:</label>
    <textarea
      id="message"
      name="message"
      placeholder="กรอกข้อความของคุณ"
    ></textarea>
  </div>

  <button type="submit">ส่งข้อมูล</button>
</form>
```

```css
.focus-form {
  max-width: 500px;
  margin: 2rem auto;
  padding: 2rem;
  background: white;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 600;
  color: #2c3e50;
}

.focus-form input,
.focus-form textarea {
  width: 100%;
  padding: 0.75rem;
  border: 2px solid #bdc3c7;
  border-radius: 4px;
  font-size: 1rem;
  transition: all 0.3s ease;
  background: #f8f9fa;
}

/* Focus styles */
.focus-form input:focus,
.focus-form textarea:focus {
  outline: none;
  border-color: #3498db;
  background: white;
  box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
  transform: translateY(-1px);
}

/* Focus styles for buttons */
.focus-form button {
  background: #2ecc71;
  color: white;
  border: none;
  padding: 0.75rem 2rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  transition: all 0.3s ease;
}

.focus-form button:focus {
  outline: none;
  box-shadow: 0 0 0 3px rgba(46, 204, 113, 0.3);
  transform: translateY(-2px);
}
```

### 1.4 :focus-visible - Focus ที่มองเห็นได้

#### ความหมาย

`:focus-visible` ใช้เลือก element ที่ได้รับ focus ผ่าน keyboard เท่านั้น ไม่รวม mouse clicks

#### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<div class="accessible-buttons">
  <button class="btn-accessible">Accessible Button</button>
  <a href="#" class="link-accessible">Accessible Link</a>
  <input type="text" class="input-accessible" placeholder="Try Tab to focus" />
</div>
```

```css
/* Remove default focus outline */
.btn-accessible,
.link-accessible,
.input-accessible {
  outline: none;
}

/* Show focus only when navigating with keyboard */
.btn-accessible:focus-visible {
  outline: 2px solid #3498db;
  outline-offset: 2px;
}

.link-accessible:focus-visible {
  outline: 2px solid #e74c3c;
  outline-offset: 2px;
  background: rgba(231, 76, 60, 0.1);
}

.input-accessible:focus-visible {
  border-color: #2ecc71;
  box-shadow: 0 0 0 3px rgba(46, 204, 113, 0.2);
}

/* Fallback for browsers that don't support :focus-visible */
.btn-accessible:focus:not(:focus-visible) {
  outline: none;
}

.link-accessible:focus:not(:focus-visible) {
  outline: none;
  background: none;
}
```

## 2. Link States Pseudo-classes

### 2.1 :visited - ลิงก์ที่เคยเยี่ยมชมแล้ว

#### ความหมาย

`:visited` ใช้เลือก links ที่ผู้ใช้เคยคลิกไปแล้ว

#### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<div class="link-examples">
  <a href="https://www.google.com">Google (External)</a>
  <a href="#section1">Internal Link</a>
  <a href="mailto:test@example.com">Email Link</a>
  <a href="tel:+66123456789">Phone Link</a>
</div>
```

```css
/* Default link styles */
.link-examples a {
  color: #3498db;
  text-decoration: none;
  padding: 0.5rem;
  margin: 0.25rem;
  display: inline-block;
  border-radius: 4px;
  transition: all 0.3s ease;
}

/* Visited link styles */
.link-examples a:visited {
  color: #9b59b6;
  background: rgba(155, 89, 182, 0.1);
}

/* Hover state for all links */
.link-examples a:hover {
  background: rgba(52, 152, 219, 0.1);
  transform: translateY(-1px);
}

/* Visited links hover */
.link-examples a:visited:hover {
  background: rgba(155, 89, 182, 0.2);
}

/* Special styling for different link types */
a[href^='mailto']:visited {
  color: #e67e22;
}

a[href^='tel']:visited {
  color: #1abc9c;
}
```

## 3. Form States Pseudo-classes

### 3.1 :checked - Elements ที่ถูกเลือก

#### ความหมาย

`:checked` ใช้เลือก input elements ประเภท checkbox, radio, หรือ option ที่ถูกเลือก

#### ตัวอย่างการใช้งาน

##### Custom Checkboxes

```html
<!-- HTML -->
<div class="custom-form">
  <div class="checkbox-group">
    <input type="checkbox" id="option1" name="options" />
    <label for="option1">Option 1</label>
  </div>

  <div class="checkbox-group">
    <input type="checkbox" id="option2" name="options" />
    <label for="option2">Option 2</label>
  </div>

  <div class="radio-group">
    <input type="radio" id="size-s" name="size" value="small" />
    <label for="size-s">Small</label>

    <input type="radio" id="size-m" name="size" value="medium" />
    <label for="size-m">Medium</label>

    <input type="radio" id="size-l" name="size" value="large" />
    <label for="size-l">Large</label>
  </div>
</div>
```

```css
/* Hide default checkboxes and radios */
.custom-form input[type='checkbox'],
.custom-form input[type='radio'] {
  display: none;
}

/* Custom checkbox styles */
.checkbox-group {
  margin-bottom: 1rem;
}

.checkbox-group label {
  display: flex;
  align-items: center;
  cursor: pointer;
  padding: 0.5rem;
  border-radius: 4px;
  transition: background-color 0.3s ease;
}

.checkbox-group label:hover {
  background: #f8f9fa;
}

.checkbox-group label::before {
  content: '';
  width: 20px;
  height: 20px;
  border: 2px solid #bdc3c7;
  border-radius: 4px;
  margin-right: 0.75rem;
  transition: all 0.3s ease;
  background: white;
}

/* Checked checkbox styles */
.checkbox-group input:checked + label::before {
  background: #2ecc71;
  border-color: #2ecc71;
  background-image: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path fill="white" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"/></svg>');
  background-repeat: no-repeat;
  background-position: center;
}

/* Radio button styles */
.radio-group {
  display: flex;
  gap: 1rem;
  margin-top: 1rem;
}

.radio-group label {
  display: flex;
  align-items: center;
  cursor: pointer;
  padding: 0.5rem 1rem;
  border: 2px solid #bdc3c7;
  border-radius: 4px;
  transition: all 0.3s ease;
}

.radio-group label::before {
  content: '';
  width: 16px;
  height: 16px;
  border: 2px solid #bdc3c7;
  border-radius: 50%;
  margin-right: 0.5rem;
  transition: all 0.3s ease;
  background: white;
}

/* Checked radio styles */
.radio-group input:checked + label {
  border-color: #3498db;
  background: rgba(52, 152, 219, 0.1);
}

.radio-group input:checked + label::before {
  border-color: #3498db;
  background: #3498db;
  box-shadow: inset 0 0 0 3px white;
}
```

##### Toggle Switches

```html
<!-- HTML -->
<div class="toggle-switches">
  <div class="toggle-group">
    <input type="checkbox" id="notifications" class="toggle" />
    <label for="notifications" class="toggle-label">
      <span class="toggle-text">การแจ้งเตือน</span>
    </label>
  </div>

  <div class="toggle-group">
    <input type="checkbox" id="dark-mode" class="toggle" />
    <label for="dark-mode" class="toggle-label">
      <span class="toggle-text">โหมดมืด</span>
    </label>
  </div>
</div>
```

```css
.toggle-group {
  margin-bottom: 1rem;
}

.toggle {
  display: none;
}

.toggle-label {
  display: flex;
  align-items: center;
  cursor: pointer;
  justify-content: space-between;
  padding: 1rem;
  background: #f8f9fa;
  border-radius: 8px;
  transition: background-color 0.3s ease;
}

.toggle-label::after {
  content: '';
  width: 50px;
  height: 26px;
  background: #bdc3c7;
  border-radius: 13px;
  position: relative;
  transition: background-color 0.3s ease;
}

.toggle-label::before {
  content: '';
  width: 22px;
  height: 22px;
  background: white;
  border-radius: 50%;
  position: absolute;
  right: 1rem;
  transform: translateX(-2px) translateY(2px);
  transition: transform 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  z-index: 1;
}

/* Checked toggle styles */
.toggle:checked + .toggle-label {
  background: rgba(46, 204, 113, 0.1);
}

.toggle:checked + .toggle-label::after {
  background: #2ecc71;
}

.toggle:checked + .toggle-label::before {
  transform: translateX(24px) translateY(2px);
}
```

### 3.2 :disabled - Elements ที่ถูกปิดใช้งาน

#### ความหมาย

`:disabled` ใช้เลือก form elements ที่มี attribute disabled

#### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<form class="disabled-form">
  <div class="form-group">
    <label for="active-input">Active Input:</label>
    <input type="text" id="active-input" placeholder="พิมพ์ได้" />
  </div>

  <div class="form-group">
    <label for="disabled-input">Disabled Input:</label>
    <input type="text" id="disabled-input" placeholder="พิมพ์ไม่ได้" disabled />
  </div>

  <div class="button-group">
    <button type="submit">Active Button</button>
    <button type="button" disabled>Disabled Button</button>
  </div>

  <div class="checkbox-group">
    <input type="checkbox" id="active-check" />
    <label for="active-check">Active Checkbox</label>

    <input type="checkbox" id="disabled-check" disabled />
    <label for="disabled-check">Disabled Checkbox</label>
  </div>
</form>
```

```css
/* Disabled input styles */
.disabled-form input:disabled {
  background: #ecf0f1;
  color: #7f8c8d;
  border-color: #bdc3c7;
  cursor: not-allowed;
  opacity: 0.6;
}

.disabled-form input:disabled::placeholder {
  color: #95a5a6;
}

/* Disabled button styles */
.disabled-form button:disabled {
  background: #95a5a6;
  color: #ecf0f1;
  cursor: not-allowed;
  opacity: 0.6;
  transform: none;
  box-shadow: none;
}

.disabled-form button:disabled:hover {
  background: #95a5a6;
  transform: none;
  box-shadow: none;
}

/* Disabled checkbox styles */
.disabled-form input[type='checkbox']:disabled + label {
  color: #7f8c8d;
  cursor: not-allowed;
  opacity: 0.6;
}

.disabled-form input[type='checkbox']:disabled + label::before {
  background: #ecf0f1;
  border-color: #bdc3c7;
}

/* Disabled label styles */
.disabled-form label:has(input:disabled) {
  color: #7f8c8d;
  cursor: not-allowed;
}
```

### 3.3 :required - Elements ที่จำเป็นต้องกรอก

#### ความหมาย

`:required` ใช้เลือก form elements ที่มี attribute required

#### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<form class="required-form">
  <div class="form-group">
    <label for="req-name">ชื่อ (จำเป็น):</label>
    <input type="text" id="req-name" name="name" required />
  </div>

  <div class="form-group">
    <label for="req-email">อีเมล (จำเป็น):</label>
    <input type="email" id="req-email" name="email" required />
  </div>

  <div class="form-group">
    <label for="opt-phone">เบอร์โทร (ไม่จำเป็น):</label>
    <input type="tel" id="opt-phone" name="phone" />
  </div>

  <button type="submit">ส่งข้อมูล</button>
</form>
```

```css
/* Required field indicator */
.required-form input:required {
  border-left: 4px solid #e74c3c;
}

.required-form input:required + label::after,
.required-form label:has(input:required)::after {
  content: ' *';
  color: #e74c3c;
  font-weight: bold;
}

/* Valid required field */
.required-form input:required:valid {
  border-left-color: #2ecc71;
}

/* Invalid required field */
.required-form input:required:invalid {
  border-left-color: #e74c3c;
  background: rgba(231, 76, 60, 0.05);
}

/* Focus state for required fields */
.required-form input:required:focus {
  box-shadow: 0 0 0 3px rgba(231, 76, 60, 0.1);
}

.required-form input:required:valid:focus {
  box-shadow: 0 0 0 3px rgba(46, 204, 113, 0.1);
}
```

## 4. Structural Pseudo-classes

### 4.1 :nth-child() - เลือกลูกตามลำดับ

#### ความหมาย

`:nth-child()` ใช้เลือก elements ตามลำดับของลูกใน parent element

#### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<div class="nth-child-examples">
  <div class="grid">
    <div class="item">Item 1</div>
    <div class="item">Item 2</div>
    <div class="item">Item 3</div>
    <div class="item">Item 4</div>
    <div class="item">Item 5</div>
    <div class="item">Item 6</div>
    <div class="item">Item 7</div>
    <div class="item">Item 8</div>
  </div>

  <table class="data-table">
    <tr>
      <td>Row 1</td>
      <td>Data 1</td>
    </tr>
    <tr>
      <td>Row 2</td>
      <td>Data 2</td>
    </tr>
    <tr>
      <td>Row 3</td>
      <td>Data 3</td>
    </tr>
    <tr>
      <td>Row 4</td>
      <td>Data 4</td>
    </tr>
    <tr>
      <td>Row 5</td>
      <td>Data 5</td>
    </tr>
  </table>
</div>
```

```css
/* Grid items */
.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1rem;
  margin-bottom: 2rem;
}

.grid .item {
  padding: 1rem;
  background: #ecf0f1;
  text-align: center;
  border-radius: 4px;
}

/* First child */
.grid .item:nth-child(1) {
  background: #e74c3c;
  color: white;
}

/* Even children */
.grid .item:nth-child(even) {
  background: #3498db;
  color: white;
}

/* Odd children */
.grid .item:nth-child(odd) {
  background: #2ecc71;
  color: white;
}

/* Every third child */
.grid .item:nth-child(3n) {
  background: #9b59b6;
  color: white;
  transform: scale(1.1);
}

/* Specific position */
.grid .item:nth-child(4) {
  background: #f39c12;
  color: white;
  border: 3px solid #e67e22;
}

/* Table rows */
.data-table {
  width: 100%;
  border-collapse: collapse;
}

.data-table td {
  padding: 0.75rem;
  border: 1px solid #bdc3c7;
}

/* Zebra striping */
.data-table tr:nth-child(even) {
  background: #f8f9fa;
}

.data-table tr:nth-child(odd) {
  background: white;
}

/* Highlight every 3rd row */
.data-table tr:nth-child(3n) {
  background: #e3f2fd;
  font-weight: bold;
}
```

### 4.2 :nth-of-type() - เลือกตามประเภทและลำดับ

#### ความหมาย

`:nth-of-type()` ใช้เลือก elements ตามประเภท (tag name) และลำดับของประเภทนั้น

#### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<div class="mixed-content">
  <h2>Heading 1</h2>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
  <h2>Heading 2</h2>
  <p>Paragraph 3</p>
  <div>Div 1</div>
  <p>Paragraph 4</p>
  <h2>Heading 3</h2>
  <div>Div 2</div>
  <p>Paragraph 5</p>
</div>
```

```css
/* First heading of its type */
.mixed-content h2:nth-of-type(1) {
  color: #e74c3c;
  border-bottom: 3px solid #e74c3c;
}

/* Every second paragraph */
.mixed-content p:nth-of-type(even) {
  background: #f8f9fa;
  padding: 1rem;
  border-left: 4px solid #3498db;
  margin: 1rem 0;
}

/* Every odd paragraph */
.mixed-content p:nth-of-type(odd) {
  background: #fff;
  padding: 1rem;
  border-left: 4px solid #2ecc71;
  margin: 1rem 0;
}

/* Last heading of its type */
.mixed-content h2:nth-of-type(3) {
  color: #9b59b6;
  background: rgba(155, 89, 182, 0.1);
  padding: 1rem;
  border-radius: 4px;
}

/* First div of its type */
.mixed-content div:nth-of-type(1) {
  background: #f39c12;
  color: white;
  padding: 1rem;
  border-radius: 4px;
  font-weight: bold;
}
```

## 5. Logical Pseudo-classes

### 5.1 :not() - ไม่ตรงตามเงื่อนไข

#### ความหมาย

`:not()` ใช้เลือก elements ที่ไม่ตรงตาม selector ที่กำหนด

#### ตัวอย่างการใช้งาน

```html
<!-- HTML -->
<div class="not-examples">
  <button class="btn">Regular Button</button>
  <button class="btn primary">Primary Button</button>
  <button class="btn secondary">Secondary Button</button>
  <button class="btn" disabled>Disabled Button</button>

  <div class="links">
    <a href="#internal">Internal Link</a>
    <a href="https://external.com">External Link</a>
    <a href="mailto:test@example.com">Email Link</a>
  </div>

  <form class="form">
    <input type="text" placeholder="Text Input" />
    <input type="email" placeholder="Email Input" />
    <input type="password" placeholder="Password Input" />
    <input type="submit" value="Submit" />
  </form>
</div>
```

```css
/* Buttons that are NOT disabled */
.not-examples button:not(:disabled) {
  cursor: pointer;
  transition: all 0.3s ease;
}

.not-examples button:not(:disabled):hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

/* Buttons that are NOT primary class */
.not-examples button:not(.primary) {
  background: #95a5a6;
  color: white;
}

/* Links that are NOT external */
.not-examples a:not([href^='https']) {
  color: #2ecc71;
  font-weight: normal;
}

.not-examples a:not([href^='https'])::before {
  content: '🏠 ';
}

/* External links */
.not-examples a[href^='https'] {
  color: #e74c3c;
  font-weight: bold;
}

.not-examples a[href^='https']::before {
  content: '🌍 ';
}

/* Input fields that are NOT submit type */
.not-examples input:not([type='submit']) {
  border: 2px solid #bdc3c7;
  padding: 0.75rem;
  margin: 0.5rem;
  border-radius: 4px;
}

.not-examples input:not([type='submit']):focus {
  border-color: #3498db;
  outline: none;
}

/* Multiple :not() selectors */
.not-examples input:not([type='submit']):not([type='password']) {
  background: #f8f9fa;
}

.not-examples input:not([type='submit']):not([type='password']):focus {
  background: white;
}
```

## Accessibility และ Best Practices

### การออกแบบที่เข้าถึงได้

```css
/* Focus indicators for accessibility */
button:focus-visible,
a:focus-visible,
input:focus-visible {
  outline: 2px solid #3498db;
  outline-offset: 2px;
}

/* High contrast mode support */
@media (prefers-contrast: high) {
  button:hover {
    outline: 2px solid currentColor;
  }
}

/* Reduced motion preference */
@media (prefers-reduced-motion: reduce) {
  *:hover,
  *:focus,
  *:active {
    transition: none;
    transform: none;
    animation: none;
  }
}

/* Color blindness considerations */
.success:not(:hover) {
  background: #2ecc71;
}

.success:hover {
  background: #27ae60;
  text-decoration: underline; /* Additional visual cue */
}

/* Touch device considerations */
@media (hover: none) {
  .card:hover {
    transform: none; /* Disable hover effects on touch devices */
  }

  .btn:hover {
    transform: none;
  }
}
```

### Performance Optimization

```css
/* Use transform instead of changing layout properties */
.btn:hover {
  transform: translateY(-2px); /* Better than top: -2px */
}

/* Use opacity for fade effects */
.overlay:hover {
  opacity: 0.8; /* Better than changing background-color */
}

/* Use will-change for animations */
.animated-element:hover {
  will-change: transform;
  transform: scale(1.1);
}

.animated-element:not(:hover) {
  will-change: auto;
}
```

## สรุป

### Pseudo-classes สำคัญ:

1. **Interactive States**: `:hover`, `:active`, `:focus`, `:focus-visible`
2. **Link States**: `:visited`, `:link`
3. **Form States**: `:checked`, `:disabled`, `:required`, `:valid`, `:invalid`
4. **Structural**: `:nth-child()`, `:nth-of-type()`, `:first-child`, `:last-child`
5. **Logical**: `:not()`, `:is()`, `:where()`

### หลักการใช้งาน:

- **ออกแบบ interactive elements** ที่ตอบสนองต่อผู้ใช้
- **ให้ feedback** ที่ชัดเจนสำหรับ user actions
- **เพิ่ม accessibility** ด้วย focus indicators
- **สร้าง patterns** ที่สม่ำเสมอใน UI
- **ใช้ animation และ transitions** อย่างเหมาะสม

### ข้อควรระวัง:

- **Performance** - ใช้ transform และ opacity สำหรับ animations
- **Accessibility** - ให้ focus indicators ที่ชัดเจน
- **Touch devices** - ปรับ hover effects สำหรับอุปกรณ์สัมผัส
- **Browser support** - ตรวจสอบการรองรับของ pseudo-classes ใหม่

การใช้ Pseudo-classes อย่างเหมาะสมจะช่วยสร้าง UI ที่ interactive, accessible และมี user experience ที่ดี!
