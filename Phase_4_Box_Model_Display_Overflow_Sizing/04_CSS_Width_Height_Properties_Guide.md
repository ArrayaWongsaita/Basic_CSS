# CSS Width และ Height Properties: คู่มือฉบับสมบูรณ์

## ภาพรวม Width และ Height Properties

Width และ Height properties เป็นพื้นฐานสำคัญในการควบคุมขนาดของ elements ใน CSS โดยมี properties หลักที่ต้องเข้าใจ ได้แก่ `width`, `height`, `min-width`, `max-width`, `min-height`, `max-height` และค่า `auto`

### โครงสร้างและความสัมพันธ์

```css
/* พื้นฐานการควบคุมขนาด */
.sizing-basics {
  /* ขนาดพื้นฐาน */
  width: 300px;
  height: 200px;

  /* ขนาดขั้นต่ำ */
  min-width: 200px;
  min-height: 150px;

  /* ขนาดสูงสุด */
  max-width: 500px;
  max-height: 400px;

  /* การทำงาน:
     min-width ≤ width ≤ max-width
     min-height ≤ height ≤ max-height
  */
}

/* ความสัมพันธ์กับ box-sizing */
.box-sizing-demo {
  box-sizing: border-box; /* แนะนำ */
  width: 300px; /* รวม padding + border แล้ว */
  padding: 20px;
  border: 2px solid #ccc;
  /* Content width = 300px - 40px - 4px = 256px */
}
```

## 1. width Property: การควบคุมความกว้าง

### ความหมายและ Values

`width` property กำหนดความกว้างของ content area ของ element (หรือ total width ถ้าใช้ border-box)

### Values และการใช้งาน

```css
/* Absolute values */
.width-absolute {
  width: 300px; /* Pixels */
  width: 20rem; /* REM units */
  width: 15em; /* EM units */
  width: 2in; /* Inches */
  width: 5cm; /* Centimeters */
  width: 50mm; /* Millimeters */
  width: 36pt; /* Points */
  width: 3pc; /* Picas */
}

/* Relative values */
.width-relative {
  width: 50%; /* Percentage ของ parent width */
  width: 80vw; /* Viewport width */
  width: 60ch; /* Character width */
  width: 100%; /* เต็มความกว้าง parent */
}

/* Auto value */
.width-auto {
  width: auto; /* ค่า default - ขึ้นกับ display type */
}

/* Modern CSS functions */
.width-modern {
  width: calc(100% - 2rem); /* คำนวณ */
  width: min(90vw, 800px); /* เลือกค่าที่เล็กกว่า */
  width: max(300px, 50%); /* เลือกค่าที่ใหญ่กว่า */
  width: clamp(300px, 50vw, 800px); /* จำกัดระหว่างค่าต่ำสุดและสูงสุด */
}

/* CSS Custom Properties */
.width-custom-properties {
  --container-width: 1200px;
  --content-width: 800px;
  --sidebar-width: 300px;

  width: var(--content-width);
  max-width: var(--container-width);
}
```

### Width ตาม Display Type

```css
/* Block elements */
.block-width {
  display: block;
  width: auto; /* Default: เต็มความกว้างของ parent */
  width: 300px; /* กำหนดความกว้างเฉพาะ */
}

/* Inline elements */
.inline-width {
  display: inline;
  width: 100px; /* ไม่มีผล - inline elements ไม่สามารถกำหนด width ได้ */
}

/* Inline-block elements */
.inline-block-width {
  display: inline-block;
  width: 200px; /* ทำงานได้ปกติ */
}

/* Flex items */
.flex-width {
  display: flex;
}

.flex-item {
  width: 200px; /* Base width */
  flex-shrink: 0; /* ป้องกันการหดตัว */
  /* หรือ */
  flex: 0 0 200px; /* flex-grow, flex-shrink, flex-basis */
}

/* Grid items */
.grid-width {
  display: grid;
  grid-template-columns: 200px 1fr 300px; /* กำหนด width ผ่าน grid */
}

.grid-item {
  width: auto; /* ตาม grid track size */
  /* หรือ */
  width: 100%; /* เต็ม grid cell */
}
```

### Responsive Width Patterns

```css
/* Container width patterns */
.container {
  width: 100%; /* Base: เต็มความกว้าง */
  max-width: 1200px; /* จำกัดความกว้างสูงสุด */
  margin: 0 auto; /* จัดกลาง */
  padding: 0 1rem; /* พื้นที่ขอบ */
}

/* Responsive containers */
.responsive-container {
  width: 100%;
  max-width: 320px; /* Mobile first */
}

@media (min-width: 768px) {
  .responsive-container {
    max-width: 768px; /* Tablet */
  }
}

@media (min-width: 1024px) {
  .responsive-container {
    max-width: 1024px; /* Desktop */
  }
}

@media (min-width: 1280px) {
  .responsive-container {
    max-width: 1280px; /* Large desktop */
  }
}

/* Fluid width with constraints */
.fluid-width {
  width: clamp(320px, 90vw, 1200px);
  /* ขั้นต่ำ 320px, ปรับตาม viewport, สูงสุด 1200px */
}

/* Content width for readability */
.content-width {
  width: 100%;
  max-width: 65ch; /* ความกว้างอ่านง่าย */
  margin: 0 auto;
}

/* Sidebar layouts */
.sidebar-layout {
  display: flex;
  width: 100%;
}

.main-content {
  width: 100%; /* ยืดหยุ่น */
  flex: 1; /* รับพื้นที่ที่เหลือ */
}

.sidebar {
  width: 300px; /* ความกว้างคงที่ */
  flex-shrink: 0; /* ไม่หดตัว */
}

/* Mobile responsive sidebar */
@media (max-width: 768px) {
  .sidebar-layout {
    flex-direction: column;
  }

  .sidebar {
    width: 100%; /* เต็มความกว้างใน mobile */
  }
}
```

## 2. min-width และ max-width: การจำกัดความกว้าง

### ความหมายและการทำงาน

`min-width` กำหนดความกว้างขั้นต่ำ ส่วน `max-width` กำหนดความกว้างสูงสุด ทำให้สามารถควบคุม responsive behavior ได้

### การใช้งาน min-width

```css
/* Basic min-width */
.min-width-basic {
  width: 50%; /* พื้นฐาน 50% ของ parent */
  min-width: 300px; /* แต่ไม่เล็กกว่า 300px */

  /* ผลลัพธ์:
     - ถ้า parent width = 800px → element width = 400px (50%)
     - ถ้า parent width = 500px → element width = 300px (min-width)
     - ถ้า parent width = 200px → element width = 300px (min-width)
  */
}

/* Responsive min-width */
.responsive-min-width {
  width: 100%;
  min-width: 320px; /* ป้องกันการเล็กเกินไป */

  /* Mobile-first design */
  @media (min-width: 768px) {
    min-width: 400px; /* เพิ่ม min-width ใน tablet+ */
  }

  @media (min-width: 1024px) {
    min-width: 500px; /* เพิ่ม min-width ใน desktop */
  }
}

/* Content min-width */
.content-min-width {
  width: 100%;
  min-width: 0; /* ยอมให้หดเล็กได้ (สำหรับ flex/grid) */
  word-wrap: break-word; /* แบ่งคำยาว */
}

/* Card min-width */
.card-min-width {
  width: 100%;
  min-width: 250px; /* การ์ดไม่เล็กเกินไป */
  max-width: 400px; /* และไม่ใหญ่เกินไป */
  margin: 0 auto;
}

/* Grid item min-width */
.grid-min-width {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  /* สร้าง columns ที่มีขนาดขั้นต่ำ 300px */
  gap: 1rem;
}

/* Flex item min-width */
.flex-min-width {
  display: flex;
}

.flex-item-min {
  flex: 1; /* ยืดหยุ่น */
  min-width: 200px; /* แต่ไม่เล็กกว่า 200px */
}
```

### การใช้งาน max-width

```css
/* Basic max-width */
.max-width-basic {
  width: 100%; /* พื้นฐาน 100% ของ parent */
  max-width: 800px; /* แต่ไม่ใหญ่กว่า 800px */
  margin: 0 auto; /* จัดกลางเมื่อถึง max-width */

  /* ผลลัพธ์:
     - ถ้า parent width = 600px → element width = 600px (100%)
     - ถ้า parent width = 1000px → element width = 800px (max-width)
  */
}

/* Container max-width patterns */
.container-max-width {
  width: 100%;
  max-width: 1200px; /* จำกัดความกว้างสูงสุด */
  margin: 0 auto; /* จัดกลาง */
  padding: 0 2rem; /* พื้นที่ขอบ */
}

/* Content max-width for readability */
.text-max-width {
  width: 100%;
  max-width: 65ch; /* ไม่เกิน 65 ตัวอักษร */
  line-height: 1.6;
  margin: 0 auto;
}

/* Image max-width */
.image-max-width {
  max-width: 100%; /* ไม่ล้นออกจาก container */
  height: auto; /* รักษาอัตราส่วน */
}

/* Modal max-width */
.modal-max-width {
  width: 90vw; /* 90% ของ viewport */
  max-width: 600px; /* แต่ไม่เกิน 600px */
  max-height: 80vh; /* จำกัดความสูงด้วย */
  margin: auto;
}

/* Responsive max-width */
.responsive-max-width {
  width: 100%;
  max-width: 400px; /* Mobile */

  @media (min-width: 768px) {
    max-width: 600px; /* Tablet */
  }

  @media (min-width: 1024px) {
    max-width: 800px; /* Desktop */
  }
}

/* Form max-width */
.form-max-width {
  width: 100%;
  max-width: 500px; /* ฟอร์มไม่กว้างเกินไป */
  margin: 0 auto;
  padding: 2rem;
}
```

### การรวม min-width และ max-width

```css
/* Complete sizing control */
.complete-sizing {
  width: 80%; /* พื้นฐาน */
  min-width: 300px; /* ขั้นต่ำ */
  max-width: 800px; /* สูงสุด */
  margin: 0 auto;

  /* Logic:
     1. เริ่มด้วย width: 80%
     2. ถ้าได้ค่าที่เล็กกว่า min-width → ใช้ min-width
     3. ถ้าได้ค่าที่ใหญ่กว่า max-width → ใช้ max-width
  */
}

/* Flexible component sizing */
.flexible-component {
  width: clamp(300px, 60vw, 800px);
  /* เทียบเท่ากับ:
     min-width: 300px;
     width: 60vw;
     max-width: 800px;
  */
}

/* Navigation responsive */
.nav-responsive {
  width: 100%;
  min-width: 320px; /* ป้องกัน mobile แคบเกินไป */
  max-width: 1200px; /* จำกัดใน desktop ใหญ่ */
  margin: 0 auto;
}

/* Card system */
.card-system {
  width: 100%;
  min-width: 280px; /* การ์ดเล็กสุด */
  max-width: 400px; /* การ์ดใหญ่สุด */
  margin: 1rem auto;
}

/* Content wrapper */
.content-wrapper {
  width: 100%;
  min-width: 0; /* ยอมให้หดได้ (สำหรับ text overflow) */
  max-width: 1000px; /* จำกัดสำหรับการอ่าน */
  margin: 0 auto;
  padding: 0 2rem;
}
```

## 3. height Property: การควบคุมความสูง

### ความหมายและ Values

`height` property กำหนดความสูงของ content area ของ element (หรือ total height ถ้าใช้ border-box)

### Height Values และการใช้งาน

```css
/* Absolute height values */
.height-absolute {
  height: 200px; /* Pixels */
  height: 15rem; /* REM units */
  height: 10em; /* EM units */
  height: 2in; /* Inches */
  height: 300mm; /* Millimeters */
}

/* Relative height values */
.height-relative {
  height: 50%; /* Percentage ของ parent height */
  height: 100vh; /* Viewport height */
  height: 50vmin; /* Viewport minimum dimension */
  height: 30vmax; /* Viewport maximum dimension */
}

/* Auto height */
.height-auto {
  height: auto; /* ค่า default - ขึ้นกับเนื้อหา */
}

/* Modern height functions */
.height-modern {
  height: calc(100vh - 80px); /* คำนวณ (viewport - header) */
  height: min(500px, 80vh); /* เลือกค่าที่เล็กกว่า */
  height: max(300px, 40vh); /* เลือกค่าที่ใหญ่กว่า */
  height: clamp(300px, 50vh, 600px); /* จำกัดระหว่างค่า */
}
```

### Height และ Parent-Child Relationship

```css
/* Parent ต้องมี height ที่กำหนดแล้ว */
.parent-height {
  height: 500px; /* กำหนดความสูงชัดเจน */
}

.child-height-percentage {
  height: 50%; /* จะได้ 250px (50% ของ 500px) */
}

/* ถ้า parent ไม่มี height กำหนด */
.parent-auto-height {
  height: auto; /* ขึ้นกับเนื้อหา */
}

.child-height-percentage-problem {
  height: 50%; /* ไม่ทำงาน - parent ไม่มี height ที่แน่นอน */
}

/* วิธีแก้: ใช้ min-height */
.parent-min-height {
  min-height: 100vh; /* อย่างน้อย full viewport */
}

.child-height-works {
  height: 50%; /* ทำงานได้ */
}

/* Flex container */
.flex-height-parent {
  display: flex;
  height: 400px;
}

.flex-height-child {
  height: 100%; /* เต็มความสูง flex container */
  /* หรือ */
  align-self: stretch; /* ยืดเต็มความสูง */
}

/* Grid container */
.grid-height-parent {
  display: grid;
  height: 500px;
  grid-template-rows: 1fr 1fr; /* แบ่งเป็น 2 แถวเท่าๆ กัน */
}

.grid-height-child {
  /* จะได้ความสูงตาม grid track */
}
```

### Common Height Patterns

```css
/* Full height layouts */
.full-height-layout {
  min-height: 100vh; /* อย่างน้อย full viewport */
  display: flex;
  flex-direction: column;
}

.header {
  height: 80px; /* ความสูงคงที่ */
  flex-shrink: 0; /* ไม่หดตัว */
}

.main-content {
  flex: 1; /* รับพื้นที่ที่เหลือ */
  min-height: 0; /* ยอมให้หดได้ */
}

.footer {
  height: 60px; /* ความสูงคงที่ */
  flex-shrink: 0; /* ไม่หดตัว */
}

/* Hero section */
.hero-section {
  height: 100vh; /* เต็มหน้าจอ */
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Card with fixed aspect ratio */
.aspect-ratio-card {
  width: 100%;
  height: 0;
  padding-bottom: 56.25%; /* 16:9 aspect ratio */
  position: relative;
}

.aspect-ratio-content {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

/* Modal height */
.modal-height {
  height: auto; /* ตามเนื้อหา */
  max-height: 80vh; /* ไม่เกิน 80% ของ viewport */
  overflow-y: auto; /* scroll ถ้าเนื้อหาเยอะ */
}

/* Sidebar height */
.sidebar-height {
  height: calc(100vh - 80px); /* Full height minus header */
  overflow-y: auto; /* scroll ถ้าเนื้อหายาว */
  position: sticky;
  top: 80px; /* stick ด้านบน */
}
```

## 4. auto Value: พฤติกรรมอัตโนมัติ

### ความหมายของ auto

`auto` เป็นค่า default ของ width และ height ที่ทำให้ browser คำนวณขนาดอัตโนมัติตาม context และ display type

### auto ใน Width

```css
/* Block elements with width: auto */
.block-auto-width {
  display: block;
  width: auto; /* Default: เต็มความกว้าง parent */
  /* เทียบเท่า width: 100% แต่ไม่นับ margin */
}

/* Inline elements with width: auto */
.inline-auto-width {
  display: inline;
  width: auto; /* ขนาดตามเนื้อหา */
  /* width: 100px ไม่มีผล กับ inline elements */
}

/* Inline-block elements with width: auto */
.inline-block-auto-width {
  display: inline-block;
  width: auto; /* ขนาดตามเนื้อหา แต่สามารถกำหนดได้ */
}

/* Flex items with width: auto */
.flex-auto-width {
  display: flex;
}

.flex-item-auto {
  width: auto; /* ขึ้นกับ flex properties */
  flex: 1; /* จะยืดเต็มพื้นที่ที่มี */
}

/* Absolutely positioned elements */
.absolute-auto-width {
  position: absolute;
  width: auto; /* ขนาดตามเนื้อหา */
  left: 50px;
  right: 50px; /* ถ้ามี left และ right, width จะคำนวณอัตโนมัติ */
}

/* Table cells */
.table-auto-width {
  display: table;
  width: 100%;
}

.table-cell-auto {
  display: table-cell;
  width: auto; /* แบ่งพื้นที่ตาม content และ constraints */
}
```

### auto ใน Height

```css
/* Most elements with height: auto */
.auto-height-basic {
  height: auto; /* Default: ขนาดตามเนื้อหา */
}

/* Container with auto height */
.container-auto-height {
  width: 100%;
  height: auto; /* ยืดตามเนื้อหาข้างใน */
  padding: 2rem;
}

/* Flex container auto height */
.flex-container-auto {
  display: flex;
  height: auto; /* ขนาดตาม flex items ที่สูงที่สุด */
}

/* Grid container auto height */
.grid-container-auto {
  display: grid;
  height: auto; /* ขนาดตาม grid content */
  grid-template-rows: auto auto auto; /* แต่ละ row ขนาดตาม content */
}

/* Image with auto height */
.image-auto-height {
  width: 100%;
  height: auto; /* รักษาอัตราส่วนเดิม */
}

/* Text content auto height */
.text-auto-height {
  width: 300px; /* จำกัดความกว้าง */
  height: auto; /* ความสูงตามจำนวนบรรทัด */
  line-height: 1.6;
}
```

### auto กับ Margin Centering

```css
/* Horizontal centering with auto margins */
.center-horizontal {
  width: 300px; /* ต้องมี width ที่กำหนด */
  margin: 0 auto; /* auto margins จะแบ่งพื้นที่เท่าๆ กัน */
}

/* Vertical centering (ใน flex context) */
.flex-center-vertical {
  display: flex;
  height: 400px;
}

.center-item {
  width: 200px;
  height: 100px;
  margin: auto; /* ทั้ง horizontal และ vertical centering */
}

/* Auto margins ใน flex */
.flex-auto-margins {
  display: flex;
  width: 100%;
}

.flex-item-left {
  width: 200px;
}

.flex-item-right {
  width: 200px;
  margin-left: auto; /* ผลัก element ไปขวาสุด */
}

/* Auto margins ใน grid */
.grid-auto-margins {
  display: grid;
  grid-template-columns: 1fr;
  height: 400px;
}

.grid-item-center {
  width: 200px;
  height: 100px;
  margin: auto; /* จัดกลางใน grid cell */
}
```

### auto กับ Position

```css
/* Auto positioning */
.auto-position {
  position: relative;
  width: auto; /* ขนาดตาม content หรือ parent */
  height: auto;

  /* Auto จะคำนวณตำแหน่งตาม normal flow */
}

/* Absolutely positioned auto */
.absolute-auto {
  position: absolute;
  width: auto; /* ขนาดตาม content */
  height: auto;
  top: 50px;
  left: 50px;
  /* right และ bottom จะเป็น auto */
}

/* Stretch with auto */
.absolute-stretch {
  position: absolute;
  top: 0;
  left: 0;
  right: 0; /* width จะเป็น auto แต่ยืดเต็ม */
  bottom: 0; /* height จะเป็น auto แต่ยืดเต็ม */
}

/* Fixed positioning auto */
.fixed-auto {
  position: fixed;
  width: auto; /* ขนาดตาม content */
  height: auto;
  top: 20px;
  right: 20px;
}
```

## 5. Modern Sizing Functions

### calc() Function

```css
/* Basic calc() usage */
.calc-basic {
  width: calc(100% - 2rem); /* 100% minus fixed margins */
  height: calc(100vh - 80px); /* Full height minus header */
}

/* Complex calc() expressions */
.calc-complex {
  width: calc((100% - 3rem) / 2); /* Half width with gaps */
  height: calc(100vh - 80px - 60px); /* Minus header and footer */
  margin: calc(1rem + 0.5vw); /* Dynamic margin */
}

/* Responsive calc() */
.calc-responsive {
  width: calc(100vw - 2rem); /* Full width minus padding */
  max-width: calc(1200px - 4rem); /* Max width minus padding */
}

/* Grid calc() */
.calc-grid {
  width: calc((100% - 2rem) / 3); /* Three columns with gaps */
  margin-right: 1rem;
}

.calc-grid:nth-child(3n) {
  margin-right: 0; /* Remove margin from last items */
}
```

### min() และ max() Functions

```css
/* min() - เลือกค่าที่เล็กกว่า */
.min-function {
  width: min(90vw, 800px); /* เล็กกว่าระหว่าง 90vw หรือ 800px */
  height: min(80vh, 600px); /* เล็กกว่าระหว่าง 80vh หรือ 600px */

  /* ประโยชน์: responsive แต่มี maximum constraint */
}

/* max() - เลือกค่าที่ใหญ่กว่า */
.max-function {
  width: max(300px, 50%); /* ใหญ่กว่าระหว่าง 300px หรือ 50% */
  height: max(200px, 30vh); /* ใหญ่กว่าระหว่าง 200px หรือ 30vh */

  /* ประโยชน์: responsive แต่มี minimum constraint */
}

/* Practical examples */
.container-modern {
  width: min(100% - 2rem, 1200px); /* Responsive with max-width และ margin */
  margin: 0 auto;
}

.sidebar-modern {
  width: max(250px, 20vw); /* Minimum 250px, หรือ 20% viewport */
}

.hero-modern {
  height: max(400px, 50vh); /* อย่างน้อย 400px แต่ responsive */
}
```

### clamp() Function

```css
/* clamp(minimum, preferred, maximum) */
.clamp-basic {
  width: clamp(300px, 50vw, 800px);
  /*
    - ขั้นต่ำ: 300px
    - ต้องการ: 50vw (50% ของ viewport width)
    - สูงสุด: 800px
  */
}

/* Typography clamp */
.clamp-typography {
  font-size: clamp(1rem, 4vw, 2.5rem);
  line-height: 1.4;
  /* Font size ที่ responsive ตาม viewport */
}

/* Container clamp */
.clamp-container {
  width: clamp(320px, 90vw, 1200px);
  margin: 0 auto;
  padding: clamp(1rem, 5vw, 3rem);
  /* ทั้ง width และ padding responsive */
}

/* Component clamp */
.clamp-component {
  width: clamp(250px, 30vw, 400px);
  height: clamp(200px, 25vh, 350px);
  /* Component ที่ responsive ทั้ง width และ height */
}

/* Grid clamp */
.clamp-grid {
  display: grid;
  grid-template-columns: repeat(
    auto-fit,
    minmax(clamp(250px, 30vw, 350px), 1fr)
  );
  gap: clamp(1rem, 3vw, 2rem);
  /* Grid ที่ responsive ทั้ง column size และ gap */
}

/* Card system clamp */
.clamp-card {
  width: clamp(280px, 90vw, 400px);
  height: auto;
  min-height: clamp(200px, 40vw, 300px);
  padding: clamp(1rem, 4vw, 2rem);
  margin: clamp(0.5rem, 2vw, 1.5rem) auto;
  /* Card ที่ responsive ทุกมิติ */
}
```

## 6. Responsive Sizing Patterns

### Mobile-First Approach

```css
/* Mobile-first sizing */
.mobile-first {
  /* Mobile (default) */
  width: 100%;
  max-width: none;

  /* Tablet */
  @media (min-width: 768px) {
    width: 80%;
    max-width: 600px;
  }

  /* Desktop */
  @media (min-width: 1024px) {
    width: 70%;
    max-width: 800px;
  }

  /* Large Desktop */
  @media (min-width: 1280px) {
    width: 60%;
    max-width: 1000px;
  }
}

/* Breakpoint-based containers */
.container-breakpoints {
  width: 100%;
  margin: 0 auto;
  padding: 0 1rem;

  /* Small devices */
  max-width: 100%;

  /* Medium devices */
  @media (min-width: 768px) {
    max-width: 750px;
    padding: 0 15px;
  }

  /* Large devices */
  @media (min-width: 992px) {
    max-width: 970px;
  }

  /* Extra large devices */
  @media (min-width: 1200px) {
    max-width: 1170px;
  }
}

/* Component responsive sizing */
.component-responsive {
  /* Base sizing */
  width: 100%;
  height: auto;
  padding: 1rem;

  /* Adjust for larger screens */
  @media (min-width: 768px) {
    width: 48%;
    display: inline-block;
    vertical-align: top;
    margin: 0 1%;
  }

  @media (min-width: 1024px) {
    width: 31.33%;
    margin: 0 1%;
  }
}
```

### Container Query Preparation

```css
/* Future-ready with container queries */
.container-query-ready {
  width: 100%;
  min-width: 0; /* ยอมให้หดตัวได้ */
  container-type: inline-size; /* เตรียมสำหรับ container queries */
}

/* Intrinsic sizing */
.intrinsic-sizing {
  width: fit-content; /* ขนาดตามเนื้อหาแต่ไม่เกิน parent */
  height: fit-content;
  max-width: 100%; /* ป้องกันล้น */
}

.intrinsic-min {
  width: min-content; /* ขนาดเล็กที่สุดที่เป็นไปได้ */
}

.intrinsic-max {
  width: max-content; /* ขนาดใหญ่ที่สุดที่เนื้อหาต้องการ */
}
```

### Grid and Flexbox Sizing

```css
/* Flexbox sizing patterns */
.flex-sizing-parent {
  display: flex;
  width: 100%;
  gap: 1rem;
}

.flex-item-fixed {
  width: 200px; /* ขนาดคงที่ */
  flex-shrink: 0; /* ไม่หดตัว */
}

.flex-item-flexible {
  flex: 1; /* ยืดหยุ่น */
  min-width: 0; /* ยอมให้หดได้ */
}

.flex-item-proportional {
  flex: 2; /* สัดส่วน 2:1 กับ item อื่น */
  min-width: 150px; /* แต่ไม่เล็กกว่า 150px */
}

/* Grid sizing patterns */
.grid-sizing {
  display: grid;
  width: 100%;
  gap: 1rem;

  /* Fixed and flexible columns */
  grid-template-columns: 200px 1fr 150px;

  /* Responsive columns */
  @media (max-width: 768px) {
    grid-template-columns: 1fr; /* Single column on mobile */
  }
}

/* Auto-fit และ minmax */
.grid-responsive {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  width: 100%;
}

/* Auto-fill pattern */
.grid-auto-fill {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 1rem;
  width: 100%;
}
```

## 7. Common Sizing Patterns และ Use Cases

### Layout Patterns

```css
/* Holy Grail Layout */
.holy-grail {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.holy-grail-header {
  height: 80px;
  flex-shrink: 0;
}

.holy-grail-main {
  flex: 1;
  display: flex;
  min-height: 0;
}

.holy-grail-content {
  flex: 1;
  min-width: 0;
}

.holy-grail-sidebar {
  width: 250px;
  flex-shrink: 0;
}

.holy-grail-footer {
  height: 60px;
  flex-shrink: 0;
}

/* Responsive Holy Grail */
@media (max-width: 768px) {
  .holy-grail-main {
    flex-direction: column;
  }

  .holy-grail-sidebar {
    width: 100%;
    order: -1; /* ย้าย sidebar ขึ้นบน */
  }
}

/* Card Grid Pattern */
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

.card-item {
  width: 100%;
  height: auto;
  min-height: 200px;
  padding: 1.5rem;
  border-radius: 0.5rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Magazine Layout */
.magazine-layout {
  display: grid;
  grid-template-columns: 2fr 1fr;
  grid-template-rows: auto auto;
  gap: 2rem;
  max-width: 1000px;
  margin: 0 auto;
}

.magazine-feature {
  grid-column: 1 / 2;
  grid-row: 1 / 3;
  min-height: 400px;
}

.magazine-sidebar-1 {
  grid-column: 2 / 3;
  grid-row: 1 / 2;
  min-height: 180px;
}

.magazine-sidebar-2 {
  grid-column: 2 / 3;
  grid-row: 2 / 3;
  min-height: 180px;
}

@media (max-width: 768px) {
  .magazine-layout {
    grid-template-columns: 1fr;
    grid-template-rows: auto auto auto;
  }

  .magazine-feature {
    grid-column: 1;
    grid-row: 1;
  }

  .magazine-sidebar-1 {
    grid-column: 1;
    grid-row: 2;
  }

  .magazine-sidebar-2 {
    grid-column: 1;
    grid-row: 3;
  }
}
```

### Component Patterns

```css
/* Modal sizing */
.modal-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal-content {
  width: clamp(320px, 90vw, 600px);
  height: auto;
  max-height: clamp(400px, 80vh, 800px);
  padding: 2rem;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
  overflow-y: auto;
}

/* Hero section sizing */
.hero-section {
  width: 100%;
  height: clamp(400px, 100vh, 800px);
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.hero-content {
  width: clamp(320px, 80vw, 800px);
  padding: 2rem;
}

/* Navigation sizing */
.navigation {
  width: 100%;
  height: 60px;
  position: sticky;
  top: 0;
  z-index: 100;
}

.nav-container {
  width: 100%;
  max-width: 1200px;
  height: 100%;
  margin: 0 auto;
  padding: 0 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

/* Form sizing */
.form-container {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  padding: 2rem;
}

.form-group {
  width: 100%;
  margin-bottom: 1.5rem;
}

.form-input {
  width: 100%;
  height: 50px;
  padding: 0 1rem;
  border: 1px solid #ddd;
  border-radius: 0.25rem;
}

.form-textarea {
  width: 100%;
  min-height: 120px;
  padding: 1rem;
  resize: vertical;
}

/* Button sizing */
.button-group {
  display: flex;
  gap: 1rem;
  width: 100%;
}

.button-primary {
  flex: 1;
  height: 50px;
  min-width: 120px;
  max-width: 200px;
}

.button-secondary {
  width: auto;
  height: 50px;
  padding: 0 2rem;
}
```

## 8. Best Practices Summary

### DO's ✅

```css
/* ✅ ใช้ border-box สำหรับการคำนวณที่ง่าย */
*,
*::before,
*::after {
  box-sizing: border-box;
}

/* ✅ ใช้ max-width สำหรับ responsive containers */
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}

/* ✅ ใช้ min-width เพื่อป้องกันการเล็กเกินไป */
.component {
  width: 100%;
  min-width: 300px;
}

/* ✅ ใช้ clamp() สำหรับ responsive sizing */
.responsive-element {
  width: clamp(300px, 50vw, 800px);
  font-size: clamp(1rem, 4vw, 2rem);
}

/* ✅ ใช้ auto สำหรับ flexible sizing */
.flexible-height {
  height: auto; /* ขนาดตามเนื้อหา */
}

/* ✅ ใช้ percentage สำหรับ responsive layouts */
.responsive-grid {
  width: 100%;
}

.grid-item {
  width: 33.33%;
}

@media (max-width: 768px) {
  .grid-item {
    width: 100%;
  }
}
```

### DON'Ts ❌

```css
/* ❌ หลีกเลี่ยง fixed dimensions ที่ไม่ responsive */
.fixed-bad {
  width: 500px; /* ไม่ responsive */
  height: 300px;
}

/* ❌ หลีกเลี่ยงการใช้ height: 100% โดยไม่มี parent height */
.height-percentage-bad {
  height: 100%; /* parent ไม่มี height กำหนด */
}

/* ❌ หลีกเลี่ยง content-box กับ percentage */
.content-box-bad {
  box-sizing: content-box;
  width: 50%;
  padding: 2rem; /* Total width > 50% */
}

/* ❌ หลีกเลี่ยง overflow โดยไม่จำเป็น */
.overflow-bad {
  width: 300px;
  height: 200px;
  /* เนื้อหาอาจล้นออกมา */
}

/* ❌ หลีกเลี่ยงการ mix units ที่ไม่สอดคล้อง */
.mixed-units-bad {
  width: 50%; /* percentage */
  max-width: 300px; /* pixels */
  min-width: 20rem; /* rem */
  /* ไม่มีความสัมพันธ์กัน */
}
```

### Quick Reference

```css
/* สูตรการใช้ width/height อย่างมีประสิทธิภาพ */

/* Container pattern */
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 clamp(1rem, 5vw, 3rem);
}

/* Component pattern */
.component {
  width: clamp(300px, 100%, 600px);
  height: auto;
  min-height: 200px;
}

/* Layout pattern */
.layout {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.layout-header {
  height: 80px;
  flex-shrink: 0;
}

.layout-main {
  flex: 1;
  min-height: 0;
}

.layout-footer {
  height: 60px;
  flex-shrink: 0;
}

/* Responsive pattern */
.responsive {
  width: 100%;

  /* Mobile first */
  max-width: none;

  @media (min-width: 768px) {
    max-width: 700px;
  }

  @media (min-width: 1024px) {
    max-width: 900px;
  }
}
```

การเข้าใจและใช้งาน Width และ Height Properties อย่างถูกต้องจะทำให้สามารถสร้าง layout ที่ responsive, flexible และใช้งานได้ดีในทุกขนาดหน้าจอ!
