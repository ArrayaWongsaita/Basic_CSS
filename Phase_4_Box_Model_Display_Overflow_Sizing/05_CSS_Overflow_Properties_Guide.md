# CSS Overflow Properties: คู่มือฉบับสมบูรณ์

## ภาพรวม Overflow Properties

`overflow` property ควบคุมการแสดงผลเมื่อเนื้อหาของ element มีขนาดใหญ่กว่า container ที่กำหนดไว้ โดยมี values หลัก 4 ค่า: `visible`, `hidden`, `scroll`, และ `auto` ซึ่งแต่ละค่ามีพฤติกรรมและการใช้งานที่แตกต่างกัน

### โครงสร้างและความสัมพันธ์

```css
/* Basic overflow syntax */
.overflow-demo {
  /* กำหนดขนาด container */
  width: 300px;
  height: 200px;
  border: 2px solid #3b82f6;

  /* Overflow behavior */
  overflow: visible; /* Default - เนื้อหาล้นออกมา */
  overflow: hidden; /* ซ่อนเนื้อหาที่ล้น */
  overflow: scroll; /* แสดง scrollbar เสมอ */
  overflow: auto; /* แสดง scrollbar เมื่อจำเป็น */
}

/* แยกแนวตั้งและแนวนอน */
.overflow-directional {
  width: 300px;
  height: 200px;

  overflow-x: hidden; /* แนวนอน */
  overflow-y: auto; /* แนวตั้ง */

  /* หรือใช้ shorthand */
  overflow: hidden auto; /* x y */
}

/* เนื้อหาที่มีขนาดใหญ่เกิน container */
.overflow-content {
  width: 500px; /* กว้างกว่า container */
  height: 400px; /* สูงกว่า container */
  background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
  padding: 1rem;
}
```

## 1. overflow: visible - การแสดงล้น (Default)

### ความหมายและพฤติกรรม

`overflow: visible` เป็นค่า default ที่ทำให้เนื้อหาที่เกินขนาด container จะแสดงล้นออกมาข้างนอก

### การใช้งานและตัวอย่าง

```css
/* Default visible behavior */
.overflow-visible {
  width: 200px;
  height: 150px;
  border: 2px solid #e74c3c;
  overflow: visible; /* ค่า default */

  /* เนื้อหาจะล้นออกมา */
  background-color: #fee2e2;
  padding: 1rem;
}

.overflow-visible-content {
  width: 300px; /* กว้างกว่า parent */
  height: 200px; /* สูงกว่า parent */
  background: #fbbf24;
  border-radius: 0.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  color: white;
}

/* ตัวอย่างการใช้งาน visible */
.tooltip-container {
  position: relative;
  width: 200px;
  height: 50px;
  overflow: visible; /* ให้ tooltip แสดงล้นออกมา */
  background: #f3f4f6;
  border-radius: 0.25rem;
}

.tooltip {
  position: absolute;
  top: -40px;
  left: 50%;
  transform: translateX(-50%);
  background: #1f2937;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 0.25rem;
  white-space: nowrap;
  font-size: 0.875rem;

  /* Arrow */
  &::after {
    content: '';
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    border: 5px solid transparent;
    border-top-color: #1f2937;
  }
}

/* Dropdown menus */
.dropdown-container {
  position: relative;
  width: 150px;
  height: 40px;
  overflow: visible; /* ให้ dropdown แสดงออกมา */
}

.dropdown-button {
  width: 100%;
  height: 100%;
  background: #3b82f6;
  color: white;
  border: none;
  border-radius: 0.25rem;
  cursor: pointer;
}

.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  width: 200px; /* กว้างกว่า parent */
  background: white;
  border: 1px solid #d1d5db;
  border-radius: 0.25rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  z-index: 100;
}

.dropdown-item {
  padding: 0.75rem 1rem;
  border-bottom: 1px solid #f3f4f6;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.dropdown-item:hover {
  background-color: #f9fafb;
}

/* Floating elements */
.floating-card {
  position: relative;
  width: 250px;
  height: 100px;
  overflow: visible; /* ให้ floating elements แสดงได้ */
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.floating-badge {
  position: absolute;
  top: -10px;
  right: -10px;
  width: 30px;
  height: 30px;
  background: #ef4444;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.75rem;
  font-weight: bold;
}
```

### เมื่อไหร่ควรใช้ visible

```css
/* ✅ เหมาะสำหรับ: */
.use-visible-when {
  /* Tooltips และ popovers */
  .tooltip-parent {
    overflow: visible;
  }

  /* Dropdown menus */
  .dropdown-parent {
    overflow: visible;
  }

  /* Floating badges/notifications */
  .badge-parent {
    overflow: visible;
  }

  /* Sticky elements */
  .sticky-parent {
    overflow: visible;
  }

  /* Animation effects ที่ต้องการแสดงนอก bounds */
  .animation-parent {
    overflow: visible;
  }
}

/* ❌ ไม่เหมาะสำหรับ: */
.avoid-visible-when {
  /* Content ที่ต้องการจำกัดขนาด */
  /* Layout ที่เข้มงวดเรื่องขนาด */
  /* Mobile responsive ที่อาจเกิดปัญหา horizontal scroll */
}
```

## 2. overflow: hidden - การซ่อนเนื้อหาล้น

### ความหมายและพฤติกรรม

`overflow: hidden` จะซ่อนเนื้อหาที่เกินขนาด container โดยไม่แสดง scrollbar

### การใช้งานและตัวอย่าง

```css
/* Basic hidden overflow */
.overflow-hidden {
  width: 200px;
  height: 150px;
  border: 2px solid #10b981;
  overflow: hidden; /* ซ่อนเนื้อหาที่ล้น */
  background-color: #d1fae5;
}

.overflow-hidden-content {
  width: 400px; /* กว้างกว่า parent */
  height: 300px; /* สูงกว่า parent */
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  font-weight: bold;
}

/* Image cropping */
.image-crop {
  width: 200px;
  height: 200px;
  overflow: hidden;
  border-radius: 50%; /* วงกลม */
  border: 4px solid white;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.image-crop img {
  width: 100%;
  height: 100%;
  object-fit: cover; /* ครอบพื้นที่ */
  object-position: center;
  transition: transform 0.3s ease;
}

.image-crop:hover img {
  transform: scale(1.1); /* ขยายเมื่อ hover */
}

/* Card with text truncation */
.card-hidden {
  width: 300px;
  height: 200px;
  overflow: hidden;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 1.5rem;
}

.card-title {
  font-size: 1.25rem;
  font-weight: bold;
  margin-bottom: 1rem;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis; /* แสดง ... เมื่อข้อความยาว */
}

.card-description {
  color: #6b7280;
  line-height: 1.6;
  /* เนื้อหาที่เกินจะถูกซ่อน */
}

/* Masonry layout items */
.masonry-item {
  width: 250px;
  overflow: hidden;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  margin-bottom: 1rem;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.masonry-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.masonry-image {
  width: 100%;
  height: 200px;
  overflow: hidden;
}

.masonry-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.masonry-item:hover .masonry-image img {
  transform: scale(1.05);
}

.masonry-content {
  padding: 1rem;
}
```

### Animation Techniques ด้วย Hidden

```css
/* Slide animations */
.slide-container {
  width: 300px;
  height: 200px;
  overflow: hidden;
  background: #f8fafc;
  border-radius: 0.5rem;
  position: relative;
}

.slide-content {
  width: 100%;
  height: 100%;
  display: flex;
  transition: transform 0.3s ease;
}

.slide-panel {
  min-width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  font-weight: bold;
  color: white;
}

.slide-panel:nth-child(1) {
  background: #ef4444;
}
.slide-panel:nth-child(2) {
  background: #10b981;
}
.slide-panel:nth-child(3) {
  background: #3b82f6;
}

/* Transform to show different panels */
.slide-content.show-second {
  transform: translateX(-100%);
}

.slide-content.show-third {
  transform: translateX(-200%);
}

/* Accordion animation */
.accordion-item {
  border: 1px solid #e5e7eb;
  border-radius: 0.25rem;
  margin-bottom: 0.5rem;
  overflow: hidden;
}

.accordion-header {
  padding: 1rem;
  background: #f9fafb;
  cursor: pointer;
  font-weight: 500;
  user-select: none;
}

.accordion-content {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease;
  background: white;
}

.accordion-content.open {
  max-height: 200px; /* หรือ auto ใน browser ที่รองรับ */
}

.accordion-inner {
  padding: 1rem;
  line-height: 1.6;
  color: #4b5563;
}

/* Text reveal animation */
.text-reveal {
  overflow: hidden;
  border-right: 2px solid #3b82f6;
  white-space: nowrap;
  animation: typing 3s steps(40, end), blink-caret 0.75s step-end infinite;
}

@keyframes typing {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}

@keyframes blink-caret {
  from,
  to {
    border-color: transparent;
  }
  50% {
    border-color: #3b82f6;
  }
}

/* Loading skeleton */
.skeleton-container {
  width: 300px;
  overflow: hidden;
  background: #f3f4f6;
  border-radius: 0.5rem;
}

.skeleton-item {
  height: 20px;
  background: linear-gradient(90deg, #f3f4f6 25%, #e5e7eb 50%, #f3f4f6 75%);
  background-size: 200% 100%;
  animation: loading 1.5s infinite;
  margin-bottom: 0.5rem;
  border-radius: 0.25rem;
}

@keyframes loading {
  0% {
    background-position: 200% 0;
  }
  100% {
    background-position: -200% 0;
  }
}
```

### เมื่อไหร่ควรใช้ hidden

```css
/* ✅ เหมาะสำหรับ: */
.use-hidden-when {
  /* Image cropping และ masking */
  .image-container {
    overflow: hidden;
    border-radius: 50%;
  }

  /* Text truncation */
  .text-truncate {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
  }

  /* Animation containers */
  .animation-container {
    overflow: hidden;
  }

  /* Card layouts ที่ต้องการขนาดคงที่ */
  .fixed-card {
    overflow: hidden;
  }

  /* Prevent horizontal scroll */
  body {
    overflow-x: hidden;
  }
}
```

## 3. overflow: scroll - การแสดง Scrollbar เสมอ

### ความหมายและพฤติกรรม

`overflow: scroll` จะแสดง scrollbar เสมอ ไม่ว่าเนื้อหาจะล้นหรือไม่

### การใช้งานและตัวอย่าง

```css
/* Basic scroll behavior */
.overflow-scroll {
  width: 300px;
  height: 200px;
  border: 2px solid #8b5cf6;
  overflow: scroll; /* แสดง scrollbar เสมอ */
  background-color: #f3e8ff;
  padding: 1rem;
}

.overflow-scroll-content {
  width: 500px; /* กว้างกว่า container */
  height: 400px; /* สูงกว่า container */
  background: linear-gradient(45deg, #f093fb 0%, #f5576c 100%);
  border-radius: 0.5rem;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
  font-weight: bold;
}

/* Code editor container */
.code-editor {
  width: 600px;
  height: 400px;
  overflow: scroll;
  background: #1e293b;
  color: #e2e8f0;
  font-family: 'Fira Code', 'Courier New', monospace;
  border-radius: 0.5rem;
  border: 1px solid #334155;
}

.code-content {
  padding: 1rem;
  white-space: pre;
  line-height: 1.6;
  min-width: 800px; /* กว้างกว่า container */
}

/* Data table container */
.table-container {
  width: 100%;
  max-width: 800px;
  height: 300px;
  overflow: scroll;
  border: 1px solid #d1d5db;
  border-radius: 0.5rem;
  background: white;
}

.data-table {
  width: 1200px; /* กว้างกว่า container */
  border-collapse: collapse;
}

.data-table th,
.data-table td {
  padding: 0.75rem;
  text-align: left;
  border-bottom: 1px solid #e5e7eb;
  white-space: nowrap;
}

.data-table th {
  background: #f9fafb;
  font-weight: 600;
  position: sticky;
  top: 0;
  z-index: 1;
}

/* Long form container */
.long-form-container {
  width: 400px;
  height: 500px;
  overflow: scroll;
  background: white;
  border: 1px solid #d1d5db;
  border-radius: 0.5rem;
  padding: 2rem;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-label {
  display: block;
  font-weight: 500;
  margin-bottom: 0.5rem;
  color: #374151;
}

.form-input {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #d1d5db;
  border-radius: 0.25rem;
  font-size: 1rem;
}

/* Chat messages container */
.chat-container {
  width: 350px;
  height: 400px;
  overflow: scroll;
  background: white;
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
  padding: 1rem;
}

.chat-message {
  margin-bottom: 1rem;
  padding: 0.75rem;
  border-radius: 0.5rem;
  max-width: 80%;
  word-wrap: break-word;
}

.chat-message.sent {
  background: #3b82f6;
  color: white;
  margin-left: auto;
  text-align: right;
}

.chat-message.received {
  background: #f3f4f6;
  color: #1f2937;
}
```

### Custom Scrollbar Styling

```css
/* Webkit scrollbar customization */
.custom-scrollbar {
  width: 300px;
  height: 200px;
  overflow: scroll;
  background: white;
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
}

/* Webkit browsers (Chrome, Safari, Edge) */
.custom-scrollbar::-webkit-scrollbar {
  width: 12px;
  height: 12px;
}

.custom-scrollbar::-webkit-scrollbar-track {
  background: #f1f5f9;
  border-radius: 6px;
}

.custom-scrollbar::-webkit-scrollbar-thumb {
  background: #cbd5e1;
  border-radius: 6px;
  border: 2px solid #f1f5f9;
}

.custom-scrollbar::-webkit-scrollbar-thumb:hover {
  background: #94a3b8;
}

.custom-scrollbar::-webkit-scrollbar-corner {
  background: #f1f5f9;
}

/* Modern CSS scrollbar styling */
.modern-scrollbar {
  width: 300px;
  height: 200px;
  overflow: scroll;
  scrollbar-width: thin; /* Firefox */
  scrollbar-color: #cbd5e1 #f1f5f9; /* Firefox */
}

/* Minimal scrollbar */
.minimal-scrollbar {
  width: 400px;
  height: 300px;
  overflow: scroll;
}

.minimal-scrollbar::-webkit-scrollbar {
  width: 6px;
  height: 6px;
}

.minimal-scrollbar::-webkit-scrollbar-track {
  background: transparent;
}

.minimal-scrollbar::-webkit-scrollbar-thumb {
  background: rgba(0, 0, 0, 0.2);
  border-radius: 3px;
}

.minimal-scrollbar::-webkit-scrollbar-thumb:hover {
  background: rgba(0, 0, 0, 0.4);
}

/* Dark theme scrollbar */
.dark-scrollbar {
  width: 300px;
  height: 200px;
  overflow: scroll;
  background: #1f2937;
  color: #e5e7eb;
}

.dark-scrollbar::-webkit-scrollbar {
  width: 10px;
  height: 10px;
}

.dark-scrollbar::-webkit-scrollbar-track {
  background: #374151;
  border-radius: 5px;
}

.dark-scrollbar::-webkit-scrollbar-thumb {
  background: #6b7280;
  border-radius: 5px;
}

.dark-scrollbar::-webkit-scrollbar-thumb:hover {
  background: #9ca3af;
}
```

### เมื่อไหร่ควรใช้ scroll

```css
/* ✅ เหมาะสำหรับ: */
.use-scroll-when {
  /* Code editors */
  .code-editor {
    overflow: scroll;
  }

  /* Data tables ที่ใหญ่ */
  .large-table-container {
    overflow: scroll;
  }

  /* Forms ที่ยาว */
  .long-form {
    overflow: scroll;
  }

  /* Chat interfaces */
  .chat-window {
    overflow: scroll;
  }

  /* Content viewers */
  .document-viewer {
    overflow: scroll;
  }
}

/* ❌ หลีกเลี่ยงเมื่อ: */
.avoid-scroll-when {
  /* เนื้อหาไม่แน่นอนว่าจะล้นหรือไม่ */
  /* UI ที่ต้องการความสะอาด (ใช้ auto แทน) */
  /* Mobile interfaces (scrollbar อาจไม่เหมาะ) */
}
```

## 4. overflow: auto - การแสดง Scrollbar เมื่อจำเป็น

### ความหมายและพฤติกรรม

`overflow: auto` จะแสดง scrollbar เฉพาะเมื่อเนื้อหาล้นออกจาก container เท่านั้น

### การใช้งานและตัวอย่าง

```css
/* Basic auto behavior */
.overflow-auto {
  width: 300px;
  height: 200px;
  border: 2px solid #f59e0b;
  overflow: auto; /* แสดง scrollbar เมื่อจำเป็น */
  background-color: #fef3c7;
  padding: 1rem;
}

/* Dynamic content container */
.dynamic-container {
  width: 400px;
  max-height: 300px;
  overflow: auto;
  background: white;
  border: 1px solid #d1d5db;
  border-radius: 0.5rem;
  padding: 1.5rem;
}

.dynamic-content {
  line-height: 1.6;
  color: #374151;
}

/* เมื่อเนื้อหาน้อย - ไม่มี scrollbar */
.short-content {
  height: 100px;
}

/* เมื่อเนื้อหาเยอะ - มี scrollbar */
.long-content {
  height: 500px;
  background: linear-gradient(180deg, #dbeafe 0%, #bfdbfe 100%);
}

/* Modal content */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal-content {
  width: 90vw;
  max-width: 600px;
  max-height: 80vh;
  overflow: auto; /* scrollbar เมื่อเนื้อหาเยอะ */
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
}

.modal-header {
  padding: 1.5rem 2rem 0;
  border-bottom: 1px solid #e5e7eb;
}

.modal-body {
  padding: 2rem;
  line-height: 1.6;
}

.modal-footer {
  padding: 0 2rem 1.5rem;
  border-top: 1px solid #e5e7eb;
  display: flex;
  justify-content: flex-end;
  gap: 1rem;
}

/* Sidebar navigation */
.sidebar-auto {
  width: 250px;
  height: 100vh;
  overflow: auto; /* scroll เมื่อเมนูเยอะ */
  background: #1f2937;
  color: white;
  padding: 1rem 0;
}

.nav-section {
  margin-bottom: 2rem;
}

.nav-title {
  padding: 0 1rem;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  color: #9ca3af;
  margin-bottom: 0.5rem;
}

.nav-item {
  display: block;
  padding: 0.75rem 1rem;
  color: #d1d5db;
  text-decoration: none;
  transition: background-color 0.2s ease;
}

.nav-item:hover {
  background-color: #374151;
  color: white;
}

.nav-item.active {
  background-color: #3b82f6;
  color: white;
}

/* Notification center */
.notification-center {
  width: 350px;
  max-height: 400px;
  overflow: auto;
  background: white;
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.notification-header {
  padding: 1rem 1.5rem;
  border-bottom: 1px solid #e5e7eb;
  font-weight: 600;
  background: #f9fafb;
}

.notification-item {
  padding: 1rem 1.5rem;
  border-bottom: 1px solid #f3f4f6;
  transition: background-color 0.2s ease;
}

.notification-item:hover {
  background-color: #f9fafb;
}

.notification-item:last-child {
  border-bottom: none;
}

.notification-title {
  font-weight: 500;
  color: #1f2937;
  margin-bottom: 0.25rem;
}

.notification-message {
  color: #6b7280;
  font-size: 0.875rem;
  line-height: 1.4;
}

.notification-time {
  color: #9ca3af;
  font-size: 0.75rem;
  margin-top: 0.5rem;
}

/* Comment section */
.comment-section {
  width: 100%;
  max-width: 600px;
  max-height: 500px;
  overflow: auto;
  background: white;
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
}

.comment-item {
  padding: 1.5rem;
  border-bottom: 1px solid #f3f4f6;
}

.comment-item:last-child {
  border-bottom: none;
}

.comment-header {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 0.75rem;
}

.comment-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: #e5e7eb;
}

.comment-author {
  font-weight: 500;
  color: #1f2937;
}

.comment-time {
  color: #6b7280;
  font-size: 0.875rem;
}

.comment-content {
  color: #374151;
  line-height: 1.6;
}
```

### Responsive Auto Overflow

```css
/* Responsive containers */
.responsive-auto {
  width: 100%;
  max-width: 800px;
  margin: 0 auto;
  overflow: auto;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

/* Mobile adjustments */
@media (max-width: 768px) {
  .responsive-auto {
    max-height: 70vh; /* จำกัดความสูงใน mobile */
    margin: 1rem;
  }
}

/* Tablet adjustments */
@media (min-width: 769px) and (max-width: 1024px) {
  .responsive-auto {
    max-height: 60vh;
  }
}

/* Desktop */
@media (min-width: 1025px) {
  .responsive-auto {
    max-height: 500px;
  }
}

/* Flexible grid container */
.flex-grid-auto {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  max-height: 600px;
  overflow: auto;
  padding: 2rem;
}

.grid-item {
  background: white;
  border-radius: 0.5rem;
  padding: 1.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

/* Dashboard widget */
.dashboard-widget {
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}

.widget-header {
  padding: 1rem 1.5rem;
  background: #f9fafb;
  border-bottom: 1px solid #e5e7eb;
  font-weight: 600;
}

.widget-content {
  max-height: 300px;
  overflow: auto;
  padding: 1rem 1.5rem;
}

.widget-item {
  padding: 0.75rem 0;
  border-bottom: 1px solid #f3f4f6;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.widget-item:last-child {
  border-bottom: none;
}
```

### เมื่อไหร่ควรใช้ auto

```css
/* ✅ เหมาะสำหรับ: (แนะนำมากที่สุด) */
.use-auto-when {
  /* Modal dialogs */
  .modal-content {
    overflow: auto;
  }

  /* Dynamic content areas */
  .content-area {
    overflow: auto;
  }

  /* Navigation sidebars */
  .sidebar {
    overflow: auto;
  }

  /* Card content */
  .card-body {
    overflow: auto;
  }

  /* Form containers */
  .form-container {
    overflow: auto;
  }

  /* General content containers */
  .container {
    overflow: auto;
  }
}

/* เป็น default choice ที่ดีที่สุดในหลายสถานการณ์ */
```

## 5. การควบคุม Overflow แยกแนว

### overflow-x และ overflow-y

```css
/* แยกควบคุมแนวนอนและแนวตั้ง */
.directional-overflow {
  width: 300px;
  height: 200px;
  border: 2px solid #6366f1;

  /* แนวนอน: ซ่อน, แนวตั้ง: auto */
  overflow-x: hidden;
  overflow-y: auto;

  background-color: #eef2ff;
  padding: 1rem;
}

/* Table with horizontal scroll */
.table-horizontal-scroll {
  width: 100%;
  max-width: 600px;
  overflow-x: auto; /* scroll แนวนอนเมื่อจำเป็น */
  overflow-y: hidden; /* ไม่ scroll แนวตั้ง */
  border: 1px solid #d1d5db;
  border-radius: 0.5rem;
}

.wide-table {
  width: 1000px; /* กว้างกว่า container */
  border-collapse: collapse;
  background: white;
}

.wide-table th,
.wide-table td {
  padding: 0.75rem 1rem;
  text-align: left;
  border-bottom: 1px solid #e5e7eb;
  white-space: nowrap;
}

.wide-table th {
  background: #f9fafb;
  font-weight: 600;
}

/* Vertical-only scroll */
.vertical-scroll-only {
  width: 400px;
  height: 300px;
  overflow-x: hidden; /* ไม่ scroll แนวนอน */
  overflow-y: auto; /* scroll แนวตั้งเมื่อจำเป็น */
  background: white;
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
  padding: 1.5rem;
}

.vertical-content {
  width: 100%; /* ไม่เกินความกว้าง container */
  line-height: 1.6;
  color: #374151;
}

/* Horizontal carousel */
.carousel-container {
  width: 400px;
  overflow-x: auto; /* scroll แนวนอนเมื่อจำเป็น */
  overflow-y: hidden; /* ไม่ scroll แนวตั้ง */
  border-radius: 0.5rem;
  background: white;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.carousel-track {
  display: flex;
  width: 1200px; /* กว้างกว่า container */
  gap: 1rem;
  padding: 1rem;
}

.carousel-item {
  min-width: 200px;
  height: 150px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 0.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-weight: bold;
  flex-shrink: 0;
}

/* Code block with horizontal scroll */
.code-horizontal {
  width: 100%;
  max-width: 600px;
  overflow-x: auto; /* scroll แนวนอนสำหรับโค้ดยาว */
  overflow-y: hidden;
  background: #1e293b;
  border-radius: 0.5rem;
  padding: 1rem;
}

.code-line {
  color: #e2e8f0;
  font-family: 'Fira Code', 'Courier New', monospace;
  white-space: nowrap; /* ไม่ให้ข้อความห่อ */
  line-height: 1.6;
}

/* Mobile responsive scroll */
.mobile-scroll {
  width: 100%;

  /* Desktop: ไม่ scroll แนวนอน */
  overflow-x: hidden;
  overflow-y: auto;
}

@media (max-width: 768px) {
  .mobile-scroll {
    /* Mobile: อนุญาตให้ scroll แนวนอนได้ */
    overflow-x: auto;
  }
}
```

### การใช้งาน Shorthand

```css
/* Shorthand syntax */
.overflow-shorthand {
  /* overflow: x y */
  overflow: hidden auto; /* x=hidden, y=auto */
  overflow: auto hidden; /* x=auto, y=hidden */
  overflow: scroll scroll; /* x=scroll, y=scroll */
  overflow: visible hidden; /* x=visible, y=hidden */
}

/* Common patterns */
.pattern-table {
  overflow: auto hidden; /* Table กับ horizontal scroll */
}

.pattern-sidebar {
  overflow: hidden auto; /* Sidebar กับ vertical scroll */
}

.pattern-modal {
  overflow: auto auto; /* Modal กับ scroll ทุกทิศทาง */
}

.pattern-carousel {
  overflow: auto hidden; /* Carousel กับ horizontal scroll */
}

.pattern-text {
  overflow: hidden auto; /* Text container กับ vertical scroll */
}
```

## 6. Advanced Overflow Techniques

### Scroll Snap

```css
/* Scroll snap for smooth scrolling */
.scroll-snap-container {
  width: 400px;
  height: 300px;
  overflow: auto;
  scroll-snap-type: y mandatory; /* แนวตั้ง */
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.scroll-snap-item {
  height: 300px;
  scroll-snap-align: start;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  font-weight: bold;
  color: white;
  border-bottom: 1px solid rgba(255, 255, 255, 0.2);
}

.scroll-snap-item:nth-child(1) {
  background: #ef4444;
}
.scroll-snap-item:nth-child(2) {
  background: #10b981;
}
.scroll-snap-item:nth-child(3) {
  background: #3b82f6;
}
.scroll-snap-item:nth-child(4) {
  background: #f59e0b;
}

/* Horizontal scroll snap */
.horizontal-scroll-snap {
  width: 400px;
  overflow-x: auto;
  overflow-y: hidden;
  scroll-snap-type: x mandatory;
  display: flex;
  gap: 1rem;
  padding: 1rem;
}

.horizontal-snap-item {
  min-width: 300px;
  height: 200px;
  scroll-snap-align: center;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 0.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-weight: bold;
  flex-shrink: 0;
}
```

### Virtual Scrolling Preparation

```css
/* Container สำหรับ virtual scrolling */
.virtual-scroll-container {
  width: 400px;
  height: 300px;
  overflow: auto;
  background: white;
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
  position: relative;
}

.virtual-scroll-content {
  position: relative;
  /* Height จะถูกกำหนดโดย JavaScript */
}

.virtual-scroll-item {
  position: absolute;
  width: 100%;
  height: 50px; /* Fixed height สำหรับ virtual scrolling */
  display: flex;
  align-items: center;
  padding: 0 1rem;
  border-bottom: 1px solid #f3f4f6;
  background: white;
  /* top จะถูกกำหนดโดย JavaScript */
}

.virtual-scroll-item:hover {
  background: #f9fafb;
}
```

### Overflow with Position Sticky

```css
/* Sticky headers with overflow */
.sticky-table-container {
  width: 100%;
  max-width: 600px;
  height: 400px;
  overflow: auto;
  border: 1px solid #d1d5db;
  border-radius: 0.5rem;
  background: white;
}

.sticky-table {
  width: 100%;
  border-collapse: collapse;
}

.sticky-header {
  position: sticky;
  top: 0;
  background: #f9fafb;
  z-index: 10;
  border-bottom: 2px solid #e5e7eb;
}

.sticky-header th {
  padding: 1rem;
  text-align: left;
  font-weight: 600;
  color: #374151;
}

.table-row td {
  padding: 1rem;
  border-bottom: 1px solid #f3f4f6;
  color: #6b7280;
}

/* Sticky sidebar in overflow container */
.content-with-sticky {
  width: 800px;
  height: 500px;
  overflow: auto;
  display: flex;
  gap: 2rem;
  padding: 2rem;
  background: #f9fafb;
}

.sticky-sidebar {
  width: 200px;
  position: sticky;
  top: 0;
  height: fit-content;
  background: white;
  border-radius: 0.5rem;
  padding: 1rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.main-content {
  flex: 1;
  background: white;
  border-radius: 0.5rem;
  padding: 2rem;
  min-height: 1000px; /* เนื้อหายาวเพื่อทดสอบ scroll */
}
```

## 7. Performance และ Best Practices

### Performance Considerations

```css
/* Optimize scrolling performance */
.optimized-scroll {
  width: 400px;
  height: 300px;
  overflow: auto;

  /* GPU acceleration */
  transform: translateZ(0);
  will-change: scroll-position;

  /* Smooth scrolling */
  scroll-behavior: smooth;

  /* Better rendering */
  -webkit-overflow-scrolling: touch; /* iOS */
}

/* Avoid layout thrashing */
.efficient-overflow {
  overflow: auto;

  /* Use transform instead of changing layout properties */
  transition: transform 0.3s ease;
}

.efficient-overflow:hover {
  transform: translateY(-2px);
}

/* Minimize repaints */
.minimal-repaint {
  overflow: hidden;

  /* Use opacity instead of visibility */
  opacity: 1;
  transition: opacity 0.3s ease;
}

.minimal-repaint.hidden {
  opacity: 0;
}
```

### Accessibility Considerations

```css
/* Keyboard navigation friendly */
.accessible-scroll {
  overflow: auto;

  /* Focus indicators */
  &:focus-within {
    outline: 2px solid #3b82f6;
    outline-offset: -2px;
  }
}

.accessible-scroll-item {
  padding: 1rem;
  transition: background-color 0.2s ease;
}

.accessible-scroll-item:focus {
  background-color: #eff6ff;
  outline: 2px solid #3b82f6;
  outline-offset: -2px;
}

/* Screen reader friendly */
.sr-scroll-info::before {
  content: 'Scrollable content area. Use arrow keys to navigate.';
  position: absolute;
  left: -9999px;
  width: 1px;
  height: 1px;
  overflow: hidden;
}

/* Reduced motion support */
@media (prefers-reduced-motion: reduce) {
  .motion-sensitive {
    scroll-behavior: auto; /* ปิด smooth scroll */
  }
}

@media (prefers-reduced-motion: no-preference) {
  .motion-sensitive {
    scroll-behavior: smooth;
  }
}
```

### Mobile Optimizations

```css
/* Touch-friendly scrolling */
.mobile-optimized {
  overflow: auto;

  /* iOS momentum scrolling */
  -webkit-overflow-scrolling: touch;

  /* Prevent overscroll bounce on some browsers */
  overscroll-behavior: contain;

  /* Touch action for better performance */
  touch-action: pan-y; /* แนวตั้งเท่านั้น */
}

.mobile-horizontal {
  overflow-x: auto;
  overflow-y: hidden;

  /* Horizontal panning */
  touch-action: pan-x;
  -webkit-overflow-scrolling: touch;
}

/* Prevent body scroll when modal is open */
.modal-open {
  overflow: hidden;
  position: fixed;
  width: 100%;
}

/* Safe area adjustments for mobile */
.mobile-safe-scroll {
  overflow: auto;
  padding-bottom: env(safe-area-inset-bottom);
  padding-left: env(safe-area-inset-left);
  padding-right: env(safe-area-inset-right);
}
```

## 8. Common Patterns และ Use Cases

### Decision Matrix

```css
/* 🎯 เมื่อไหร่ควรใช้ overflow value ไหน */

/* ใช้ visible เมื่อ: */
.use-visible {
  /* ✅ Tooltips, dropdowns, floating elements */
  /* ✅ Animations ที่ต้องการแสดงนอก bounds */
  /* ✅ Sticky elements */
  overflow: visible;
}

/* ใช้ hidden เมื่อ: */
.use-hidden {
  /* ✅ Image cropping, masking effects */
  /* ✅ Animation containers */
  /* ✅ Text truncation */
  /* ✅ Prevent unwanted scroll */
  overflow: hidden;
}

/* ใช้ scroll เมื่อ: */
.use-scroll {
  /* ✅ Code editors, text editors */
  /* ✅ Large data tables */
  /* ✅ เมื่อต้องการ scrollbar เสมอ */
  overflow: scroll;
}

/* ใช้ auto เมื่อ: (แนะนำมากที่สุด) */
.use-auto {
  /* ✅ Modal dialogs */
  /* ✅ Content areas ทั่วไป */
  /* ✅ Navigation sidebars */
  /* ✅ Dynamic content */
  /* ✅ Cards, containers */
  overflow: auto;
}
```

### Complete Examples

```css
/* Dashboard layout */
.dashboard {
  display: grid;
  grid-template-areas:
    'header header'
    'sidebar main';
  grid-template-rows: auto 1fr;
  grid-template-columns: 250px 1fr;
  height: 100vh;
  overflow: hidden; /* ป้องกัน body scroll */
}

.dashboard-header {
  grid-area: header;
  height: 60px;
  background: white;
  border-bottom: 1px solid #e5e7eb;
  overflow: visible; /* สำหรับ dropdown menus */
}

.dashboard-sidebar {
  grid-area: sidebar;
  background: #1f2937;
  overflow-y: auto; /* scroll เมื่อเมนูเยอะ */
  overflow-x: hidden;
}

.dashboard-main {
  grid-area: main;
  padding: 2rem;
  overflow: auto; /* scroll เมื่อเนื้อหาเยอะ */
  background: #f9fafb;
}

/* E-commerce product grid */
.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 2rem;
  max-height: 600px;
  overflow: auto;
  padding: 2rem;
}

.product-card {
  background: white;
  border-radius: 0.5rem;
  overflow: hidden; /* สำหรับ image cropping */
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s ease;
}

.product-card:hover {
  transform: translateY(-4px);
}

.product-image {
  width: 100%;
  height: 200px;
  overflow: hidden;
}

.product-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.product-card:hover .product-image img {
  transform: scale(1.05);
}

.product-info {
  padding: 1rem;
  overflow: hidden; /* ป้องกันข้อความยาว */
}

.product-title {
  font-weight: 600;
  margin-bottom: 0.5rem;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

/* Chat application */
.chat-app {
  display: flex;
  height: 100vh;
  overflow: hidden;
}

.chat-sidebar {
  width: 300px;
  background: white;
  border-right: 1px solid #e5e7eb;
  overflow-y: auto;
  overflow-x: hidden;
}

.chat-main {
  flex: 1;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.chat-messages {
  flex: 1;
  overflow-y: auto;
  overflow-x: hidden;
  padding: 1rem;
  background: #f9fafb;
}

.chat-input-area {
  padding: 1rem;
  background: white;
  border-top: 1px solid #e5e7eb;
  overflow: visible; /* สำหรับ emoji picker */
}
```

## สรุป Best Practices

### 1. เลือกใช้ค่าที่เหมาะสม

- **auto**: Default choice ที่ดีที่สุดในหลายสถานการณ์
- **hidden**: สำหรับ cropping, animation, หรือป้องกัน scroll
- **visible**: สำหรับ tooltips, dropdowns, floating elements
- **scroll**: เมื่อต้องการ scrollbar เสมอ (น้อยใช้)

### 2. Performance

- ใช้ `transform: translateZ(0)` สำหรับ GPU acceleration
- หลีกเลี่ยงการเปลี่ยน overflow ใน animation
- ใช้ `will-change: scroll-position` สำหรับ smooth scrolling

### 3. Accessibility

- รองรับ keyboard navigation
- ใช้ appropriate ARIA labels
- รองรับ `prefers-reduced-motion`

### 4. Mobile Considerations

- ใช้ `-webkit-overflow-scrolling: touch` สำหรับ iOS
- ใช้ `touch-action` ที่เหมาะสม
- ใช้ `overscroll-behavior` เพื่อควบคุม overscroll

### 5. ใช้งานร่วมกับ Properties อื่น

- `position: sticky` ใน scroll containers
- `scroll-snap` สำหรับ smooth UX
- `scroll-behavior: smooth` สำหรับ smooth scrolling

การเข้าใจและใช้งาน Overflow Properties อย่างถูกต้องจะช่วยสร้าง UX ที่ดีและการควบคุม layout ที่มีประสิทธิภาพ!
