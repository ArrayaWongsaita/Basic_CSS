# CSS Specificity และ Interactive States: Exercise ปุ่มสามสถานะ

## ภาพรวม CSS Specificity

CSS Specificity เป็นระบบการคำนวณน้ำหนักของ CSS selectors เพื่อกำหนดว่า style ไหนจะถูกนำไปใช้เมื่อมี rules หลายตัวที่ชี้ไปยัง element เดียวกัน

### ระบบการคำนวณ Specificity

```
Specificity = (inline-styles, IDs, Classes/Attributes/Pseudo-classes, Elements/Pseudo-elements)
```

| Selector Type                       | Weight | Examples                          |
| ----------------------------------- | ------ | --------------------------------- |
| Inline styles                       | 1000   | `style="color: red"`              |
| IDs                                 | 100    | `#header`, `#nav`                 |
| Classes, Attributes, Pseudo-classes | 10     | `.btn`, `[type="text"]`, `:hover` |
| Elements, Pseudo-elements           | 1      | `div`, `p`, `::before`            |

### ตัวอย่างการคำนวณ Specificity

```css
/* Specificity: 0,0,0,1 = 1 */
p {
  color: black;
}

/* Specificity: 0,0,1,0 = 10 */
.text {
  color: blue;
}

/* Specificity: 0,0,1,1 = 11 */
p.text {
  color: green;
}

/* Specificity: 0,0,2,1 = 21 */
p.text.highlight {
  color: yellow;
}

/* Specificity: 0,1,0,0 = 100 */
#content {
  color: red;
}

/* Specificity: 0,1,1,1 = 111 */
#content p.text {
  color: purple;
}

/* Specificity: 0,0,2,0 = 20 */
.btn:hover {
  background: blue;
}

/* Specificity: 0,0,3,0 = 30 */
.btn.primary:hover {
  background: green;
}
```

### การเรียงลำดับความสำคัญ

```css
/* 1. !important มีความสำคัญสูงสุด */
p {
  color: red !important; /* จะชนะทุกอย่าง */
}

/* 2. Inline styles */
/* <p style="color: blue;"> */

/* 3. IDs */
#special {
  color: green;
}

/* 4. Classes, Pseudo-classes, Attributes */
.highlight:hover {
  color: yellow;
}

/* 5. Elements และ Pseudo-elements */
p::first-letter {
  color: orange;
}
```

## Pseudo-classes กับ Interactive States

### หลัก Pseudo-classes สำหรับ Interactive Elements

```css
/* Link states - ต้องเรียงตาม LVHA order */
a:link {
  /* ลิงก์ที่ยังไม่เคยเยี่ยมชม */
  color: blue;
}

a:visited {
  /* ลิงก์ที่เยี่ยมชมแล้ว */
  color: purple;
}

a:hover {
  /* เมื่อ mouse hover */
  color: red;
}

a:active {
  /* เมื่อกำลังคลิก */
  color: orange;
}

/* Form states */
input:focus {
  /* เมื่อ focus */
  border-color: blue;
}

input:disabled {
  /* เมื่อ disabled */
  background: gray;
}

input:checked {
  /* checkbox/radio ที่ถูกเลือก */
  background: green;
}

/* UI states */
:hover {
  /* mouse อยู่เหนือ element */
  opacity: 0.8;
}

:focus {
  /* element ได้รับ focus */
  outline: 2px solid blue;
}

:active {
  /* element กำลังถูกกด */
  transform: scale(0.98);
}
```

### ลำดับความสำคัญของ States (Cascade Order)

```css
/* ❌ ผิด: hover ถูกเขียนทับโดย link */
a:link {
  color: blue;
}
a:hover {
  color: red;
}
a:visited {
  color: purple;
}

/* ✅ ถูก: ใช้ LVHA order */
a:link {
  color: blue;
}
a:visited {
  color: purple;
}
a:hover {
  color: red;
}
a:active {
  color: orange;
}
```

## Exercise: ปุ่มสามสถานะ (Hover/Focus/Disabled)

### HTML Structure

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Button States Exercise</title>
    <link rel="stylesheet" href="button-styles.css" />
  </head>
  <body>
    <div class="container">
      <h1>CSS Button States Exercise</h1>

      <!-- Basic Buttons -->
      <section class="button-group">
        <h2>1. Basic Buttons</h2>
        <button class="btn btn-primary">Primary Button</button>
        <button class="btn btn-secondary">Secondary Button</button>
        <button class="btn btn-success">Success Button</button>
        <button class="btn btn-danger">Danger Button</button>
      </section>

      <!-- Size Variations -->
      <section class="button-group">
        <h2>2. Size Variations</h2>
        <button class="btn btn-primary btn-small">Small</button>
        <button class="btn btn-primary btn-medium">Medium</button>
        <button class="btn btn-primary btn-large">Large</button>
      </section>

      <!-- Disabled States -->
      <section class="button-group">
        <h2>3. Disabled States</h2>
        <button class="btn btn-primary" disabled>Disabled Primary</button>
        <button class="btn btn-secondary" disabled>Disabled Secondary</button>
        <button class="btn btn-success" disabled>Disabled Success</button>
        <button class="btn btn-danger" disabled>Disabled Danger</button>
      </section>

      <!-- Special Effects -->
      <section class="button-group">
        <h2>4. Special Effects</h2>
        <button class="btn btn-gradient">Gradient Button</button>
        <button class="btn btn-outline">Outline Button</button>
        <button class="btn btn-glow">Glow Effect</button>
        <button class="btn btn-3d">3D Button</button>
      </section>

      <!-- Loading States -->
      <section class="button-group">
        <h2>5. Loading States</h2>
        <button class="btn btn-primary btn-loading">
          <span class="btn-text">Loading...</span>
          <span class="btn-spinner"></span>
        </button>
        <button class="btn btn-secondary btn-loading" disabled>
          <span class="btn-text">Processing</span>
          <span class="btn-spinner"></span>
        </button>
      </section>

      <!-- Icon Buttons -->
      <section class="button-group">
        <h2>6. Icon Buttons</h2>
        <button class="btn btn-primary btn-icon">
          <span class="icon">💾</span>
          <span class="text">Save</span>
        </button>
        <button class="btn btn-danger btn-icon">
          <span class="icon">🗑️</span>
          <span class="text">Delete</span>
        </button>
        <button class="btn btn-success btn-icon">
          <span class="icon">✅</span>
          <span class="text">Confirm</span>
        </button>
      </section>

      <!-- Interactive Demo -->
      <section class="button-group">
        <h2>7. Interactive State Demo</h2>
        <div class="state-demo">
          <button class="btn btn-demo" id="demoBtn">Demo Button</button>
          <div class="state-info">
            <p>Current State: <span id="currentState">normal</span></p>
            <p>Specificity: <span id="specificity">0,0,1,0</span></p>
          </div>
        </div>
      </section>
    </div>

    <script src="button-demo.js"></script>
  </body>
</html>
```

### CSS Styles (button-styles.css)

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
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  min-height: 100vh;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

h1 {
  text-align: center;
  margin-bottom: 3rem;
  color: #2c3e50;
  font-size: 2.5rem;
}

h2 {
  margin-bottom: 1.5rem;
  color: #34495e;
  border-bottom: 2px solid #3498db;
  padding-bottom: 0.5rem;
}

.button-group {
  background: white;
  padding: 2rem;
  margin-bottom: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

/* Base Button Styles - Specificity: 0,0,1,0 = 10 */
.btn {
  display: inline-block;
  padding: 0.75rem 1.5rem;
  margin: 0.5rem;
  border: none;
  border-radius: 6px;
  font-size: 1rem;
  font-weight: 500;
  text-decoration: none;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  outline: none;
  background: #6c757d;
  color: white;
}

/* Hover State - Specificity: 0,0,2,0 = 20 */
.btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
}

/* Focus State - Specificity: 0,0,2,0 = 20 */
.btn:focus {
  box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.4);
  transform: translateY(-1px);
}

/* Active State - Specificity: 0,0,2,0 = 20 */
.btn:active {
  transform: translateY(1px);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

/* Disabled State - Specificity: 0,0,2,0 = 20 */
.btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
  transform: none !important;
  box-shadow: none !important;
  pointer-events: none;
}

/* Color Variants - Specificity: 0,0,2,0 = 20 */
.btn.btn-primary {
  background: linear-gradient(45deg, #3498db, #2980b9);
}

.btn.btn-primary:hover {
  background: linear-gradient(45deg, #2980b9, #1f618d);
}

.btn.btn-primary:focus {
  box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.4);
}

.btn.btn-secondary {
  background: linear-gradient(45deg, #95a5a6, #7f8c8d);
}

.btn.btn-secondary:hover {
  background: linear-gradient(45deg, #7f8c8d, #6c7b7d);
}

.btn.btn-success {
  background: linear-gradient(45deg, #2ecc71, #27ae60);
}

.btn.btn-success:hover {
  background: linear-gradient(45deg, #27ae60, #1e8449);
}

.btn.btn-danger {
  background: linear-gradient(45deg, #e74c3c, #c0392b);
}

.btn.btn-danger:hover {
  background: linear-gradient(45deg, #c0392b, #a93226);
}

/* Size Variants - Specificity: 0,0,2,0 = 20 */
.btn.btn-small {
  padding: 0.5rem 1rem;
  font-size: 0.875rem;
}

.btn.btn-medium {
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
}

.btn.btn-large {
  padding: 1rem 2rem;
  font-size: 1.125rem;
}

/* Special Effects */

/* Gradient Button - Specificity: 0,0,2,0 = 20 */
.btn.btn-gradient {
  background: linear-gradient(45deg, #667eea 0%, #764ba2 100%);
  position: relative;
}

.btn.btn-gradient::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    45deg,
    transparent 30%,
    rgba(255, 255, 255, 0.3) 50%,
    transparent 70%
  );
  transition: left 0.5s ease;
}

.btn.btn-gradient:hover::before {
  left: 100%;
}

/* Outline Button - Specificity: 0,0,2,0 = 20 */
.btn.btn-outline {
  background: transparent;
  border: 2px solid #3498db;
  color: #3498db;
}

.btn.btn-outline:hover {
  background: #3498db;
  color: white;
}

.btn.btn-outline:focus {
  box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.2);
}

/* Glow Effect - Specificity: 0,0,2,0 = 20 */
.btn.btn-glow {
  background: linear-gradient(45deg, #ff6b6b, #ee5a24);
  box-shadow: 0 0 20px rgba(255, 107, 107, 0.4);
}

.btn.btn-glow:hover {
  box-shadow: 0 0 30px rgba(255, 107, 107, 0.6);
  transform: translateY(-3px);
}

/* 3D Button - Specificity: 0,0,2,0 = 20 */
.btn.btn-3d {
  background: linear-gradient(45deg, #ff9ff3, #f368e0);
  box-shadow: 0 6px 0 #d63384, 0 8px 6px rgba(0, 0, 0, 0.3);
  border-radius: 8px;
}

.btn.btn-3d:hover {
  transform: translateY(-1px);
  box-shadow: 0 7px 0 #d63384, 0 9px 8px rgba(0, 0, 0, 0.3);
}

.btn.btn-3d:active {
  transform: translateY(3px);
  box-shadow: 0 3px 0 #d63384, 0 4px 3px rgba(0, 0, 0, 0.3);
}

/* Loading State - Specificity: 0,0,2,0 = 20 */
.btn.btn-loading {
  position: relative;
  color: transparent;
}

.btn.btn-loading .btn-text {
  opacity: 0;
}

.btn.btn-loading .btn-spinner {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 20px;
  height: 20px;
  border: 2px solid transparent;
  border-top: 2px solid white;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% {
    transform: translate(-50%, -50%) rotate(0deg);
  }
  100% {
    transform: translate(-50%, -50%) rotate(360deg);
  }
}

/* Icon Buttons - Specificity: 0,0,2,0 = 20 */
.btn.btn-icon {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.btn.btn-icon .icon {
  font-size: 1.2em;
}

/* State Demo Section */
.state-demo {
  display: flex;
  align-items: center;
  gap: 2rem;
  flex-wrap: wrap;
}

.btn.btn-demo {
  background: linear-gradient(45deg, #4ecdc4, #44a08d);
  font-size: 1.2rem;
  padding: 1rem 2rem;
  transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

/* Demo Button States with Higher Specificity */
.btn.btn-demo:hover {
  background: linear-gradient(45deg, #44a08d, #093637);
  transform: translateY(-4px) scale(1.05);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
}

.btn.btn-demo:focus {
  box-shadow: 0 0 0 4px rgba(78, 205, 196, 0.4);
  outline: none;
}

.btn.btn-demo:active {
  transform: translateY(-1px) scale(1.02);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.state-info {
  background: #f8f9fa;
  padding: 1rem;
  border-radius: 8px;
  border-left: 4px solid #3498db;
}

.state-info p {
  margin-bottom: 0.5rem;
  font-weight: 500;
}

.state-info span {
  color: #e74c3c;
  font-weight: bold;
}

/* Responsive Design */
@media (max-width: 768px) {
  .container {
    padding: 1rem;
  }

  .btn {
    margin: 0.25rem;
    padding: 0.6rem 1.2rem;
  }

  .state-demo {
    flex-direction: column;
    align-items: flex-start;
  }

  h1 {
    font-size: 2rem;
  }
}

/* Accessibility Improvements */
@media (prefers-reduced-motion: reduce) {
  .btn {
    transition: none;
  }

  .btn-spinner {
    animation: none;
  }
}

/* High Contrast Mode */
@media (prefers-contrast: high) {
  .btn {
    border: 2px solid currentColor;
  }

  .btn:focus {
    outline: 3px solid currentColor;
    outline-offset: 2px;
  }
}

/* Focus Visible for Better Accessibility */
.btn:focus-visible {
  outline: 2px solid #3498db;
  outline-offset: 2px;
}
```

### JavaScript Demo (button-demo.js)

```javascript
// filepath: /Users/non/Documents/TEACHER/CSS/Phase_2_Selectors/button-demo.js
document.addEventListener('DOMContentLoaded', function () {
  const demoBtn = document.getElementById('demoBtn');
  const currentState = document.getElementById('currentState');
  const specificity = document.getElementById('specificity');

  // State tracking
  const states = {
    normal: { text: 'normal', spec: '0,0,2,0 (btn.btn-demo)' },
    hover: { text: 'hover', spec: '0,0,3,0 (btn.btn-demo:hover)' },
    focus: { text: 'focus', spec: '0,0,3,0 (btn.btn-demo:focus)' },
    active: { text: 'active', spec: '0,0,3,0 (btn.btn-demo:active)' },
    disabled: { text: 'disabled', spec: '0,0,2,0 (btn:disabled)' },
  };

  // Event listeners for state changes
  demoBtn.addEventListener('mouseenter', () => {
    updateStateInfo('hover');
  });

  demoBtn.addEventListener('mouseleave', () => {
    if (!demoBtn.matches(':focus')) {
      updateStateInfo('normal');
    }
  });

  demoBtn.addEventListener('focus', () => {
    updateStateInfo('focus');
  });

  demoBtn.addEventListener('blur', () => {
    updateStateInfo('normal');
  });

  demoBtn.addEventListener('mousedown', () => {
    updateStateInfo('active');
  });

  demoBtn.addEventListener('mouseup', () => {
    if (demoBtn.matches(':hover')) {
      updateStateInfo('hover');
    } else if (demoBtn.matches(':focus')) {
      updateStateInfo('focus');
    } else {
      updateStateInfo('normal');
    }
  });

  function updateStateInfo(state) {
    currentState.textContent = states[state].text;
    specificity.textContent = states[state].spec;

    // Add visual feedback
    currentState.style.color = getStateColor(state);
    specificity.style.color = getStateColor(state);
  }

  function getStateColor(state) {
    const colors = {
      normal: '#6c757d',
      hover: '#3498db',
      focus: '#f39c12',
      active: '#e74c3c',
      disabled: '#95a5a6',
    };
    return colors[state] || '#6c757d';
  }

  // Demo button toggle disabled state
  let clickCount = 0;
  demoBtn.addEventListener('click', () => {
    clickCount++;
    if (clickCount >= 5) {
      demoBtn.disabled = true;
      updateStateInfo('disabled');
      demoBtn.textContent = 'Disabled (clicked 5 times)';

      // Re-enable after 3 seconds
      setTimeout(() => {
        demoBtn.disabled = false;
        demoBtn.textContent = 'Demo Button';
        clickCount = 0;
        updateStateInfo('normal');
      }, 3000);
    } else {
      demoBtn.textContent = `Demo Button (${clickCount}/5)`;
    }
  });

  // Specificity calculator demo
  const specificityExamples = [
    { selector: 'button', spec: '0,0,0,1', weight: 1 },
    { selector: '.btn', spec: '0,0,1,0', weight: 10 },
    { selector: 'button.btn', spec: '0,0,1,1', weight: 11 },
    { selector: '.btn:hover', spec: '0,0,2,0', weight: 20 },
    { selector: '#myBtn', spec: '0,1,0,0', weight: 100 },
    { selector: '#myBtn.btn', spec: '0,1,1,0', weight: 110 },
    { selector: '#myBtn.btn:hover', spec: '0,1,2,0', weight: 120 },
  ];

  // Create specificity table
  createSpecificityTable();

  function createSpecificityTable() {
    const table = document.createElement('table');
    table.style.cssText = `
            width: 100%;
            border-collapse: collapse;
            margin-top: 1rem;
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        `;

    const thead = document.createElement('thead');
    thead.innerHTML = `
            <tr style="background: #3498db; color: white;">
                <th style="padding: 1rem; text-align: left;">Selector</th>
                <th style="padding: 1rem; text-align: center;">Specificity</th>
                <th style="padding: 1rem; text-align: center;">Weight</th>
                <th style="padding: 1rem; text-align: center;">Wins Against</th>
            </tr>
        `;

    const tbody = document.createElement('tbody');
    specificityExamples.forEach((example, index) => {
      const row = document.createElement('tr');
      row.style.backgroundColor = index % 2 === 0 ? '#f8f9fa' : 'white';

      const winsAgainst =
        specificityExamples
          .filter((e) => e.weight < example.weight)
          .map((e) => e.selector)
          .join(', ') || 'None';

      row.innerHTML = `
                <td style="padding: 0.75rem; font-family: monospace; background: #f1f2f6; color: #2c3e50;">${example.selector}</td>
                <td style="padding: 0.75rem; text-align: center; font-weight: bold; color: #e74c3c;">${example.spec}</td>
                <td style="padding: 0.75rem; text-align: center; font-weight: bold; color: #2ecc71;">${example.weight}</td>
                <td style="padding: 0.75rem; text-align: center; font-size: 0.9em; color: #7f8c8d;">${winsAgainst}</td>
            `;
      tbody.appendChild(row);
    });

    table.appendChild(thead);
    table.appendChild(tbody);

    // Add table to the last section
    const lastSection = document.querySelector('.button-group:last-child');
    if (lastSection) {
      const tableTitle = document.createElement('h3');
      tableTitle.textContent = 'Specificity Comparison Table';
      tableTitle.style.marginTop = '2rem';
      tableTitle.style.color = '#2c3e50';
      lastSection.appendChild(tableTitle);
      lastSection.appendChild(table);
    }
  }
});
```

## Specificity Best Practices

### 1. เขียน CSS แบบ Low Specificity

```css
/* ✅ ดี: เริ่มจาก specificity ต่ำ */
.btn {
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 4px;
}

/* ✅ ดี: เพิ่ม specificity เมื่อจำเป็น */
.btn.btn-primary {
  background: blue;
}

.btn.btn-primary:hover {
  background: darkblue;
}

/* ❌ หลีกเลี่ยง: specificity สูงตั้งแต่แรก */
#header .nav .btn.primary {
  background: blue;
}
```

### 2. ใช้ Methodology เช่น BEM

```css
/* BEM Methodology */
.button {
  /* Block */
  /* base styles */
}

.button--primary {
  /* Block + Modifier */
  /* primary variant */
}

.button--primary:hover {
  /* Block + Modifier + State */
  /* primary hover state */
}

.button__icon {
  /* Block + Element */
  /* icon inside button */
}
```

### 3. การจัดการ !important

```css
/* ❌ หลีกเลี่ยง: ใช้ !important ไม่จำเป็น */
.btn {
  background: blue !important;
}

/* ✅ ดี: ใช้ !important เฉพาะเมื่อจำเป็น */
.utility-hidden {
  display: none !important; /* Utility class ที่ต้องแน่ใจว่าจะทำงาน */
}

.accessibility-focus:focus {
  outline: 2px solid red !important; /* เพื่อ accessibility */
}
```

### 4. State Management Pattern

```css
/* Pattern สำหรับจัดการ states */
.component {
  /* default state */
}

.component:hover {
  /* hover state */
}

.component:focus {
  /* focus state */
}

.component:active {
  /* active state */
}

.component.is-disabled,
.component:disabled {
  /* disabled state */
}

.component.is-loading {
  /* loading state */
}

.component.is-success {
  /* success state */
}

.component.is-error {
  /* error state */
}
```

## การทดสอบและ Debug Specificity

### 1. Chrome DevTools

```
1. เปิด Developer Tools (F12)
2. ไปที่ tab "Elements"
3. เลือก element ที่ต้องการดู
4. ใน Styles panel จะเห็น:
   - Computed styles
   - Cascaded styles
   - Specificity conflicts
```

### 2. CSS Specificity Calculator

```javascript
// Simple specificity calculator
function calculateSpecificity(selector) {
  const ids = (selector.match(/#[a-zA-Z][\w-]*/g) || []).length;
  const classes = (selector.match(/\.[a-zA-Z][\w-]*/g) || []).length;
  const attributes = (selector.match(/\[[^\]]*\]/g) || []).length;
  const pseudoClasses = (selector.match(/:[a-zA-Z][\w-()]*/g) || []).length;
  const elements =
    (selector.match(/[a-zA-Z][\w-]*/g) || []).length - classes - ids;

  return {
    ids,
    classes: classes + attributes + pseudoClasses,
    elements,
    specificity: `${ids},${classes + attributes + pseudoClasses},${elements}`,
    weight: ids * 100 + (classes + attributes + pseudoClasses) * 10 + elements,
  };
}

// ตัวอย่างการใช้งาน
console.log(calculateSpecificity('.btn.btn-primary:hover'));
// Output: { ids: 0, classes: 3, elements: 0, specificity: "0,3,0", weight: 30 }
```

## สรุป Key Points

### 1. Specificity Hierarchy

- **Inline styles** (1000) > **IDs** (100) > **Classes/Pseudo-classes** (10) > **Elements** (1)
- **!important** มีความสำคัญสูงสุด แต่ควรหลีกเลี่ยง

### 2. Interactive States Best Practices

- ใช้ **LVHA order** สำหรับ links: `:link` → `:visited` → `:hover` → `:active`
- **:focus** สำคัญสำหรับ accessibility
- **:disabled** ควรมี visual feedback ที่ชัดเจน

### 3. Button States Checklist

- ✅ **Default state**: สีพื้นฐาน, typography ที่อ่านง่าย
- ✅ **Hover state**: feedback เมื่อ mouse อยู่เหนือ
- ✅ **Focus state**: outline หรือ visual cue สำหรับ keyboard navigation
- ✅ **Active state**: feedback เมื่อกำลังกด
- ✅ **Disabled state**: visual indication ที่ชัดเจน
- ✅ **Loading state**: animation หรือ spinner

### 4. Performance Tips

- ใช้ **transform** แทน position changes
- ใช้ **will-change** สำหรับ animations ที่ซับซ้อน
- ลบ **will-change** หลังจาก animation เสร็จ

### 5. Accessibility Considerations

- รองรับ **keyboard navigation**
- ใช้ **focus-visible** สำหรับ modern browsers
- เคารพ **prefers-reduced-motion**
- รองรับ **high contrast mode**

การเรียนรู้ Specificity และ Interactive States เป็นพื้นฐานสำคัญสำหรับการเขียน CSS ที่มีประสิทธิภาพและใช้งานได้ดี!
