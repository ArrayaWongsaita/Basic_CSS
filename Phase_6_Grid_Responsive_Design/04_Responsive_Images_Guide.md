# Responsive Images: การทำให้รูปภาพปรับตัวตามหน้าจอ

## ภาพรวม Responsive Images

**Responsive Images** คือเทคนิคการทำให้รูปภาพปรับขนาดตามขนาดของ container หรือหน้าจอโดยอัตโนมัติ เพื่อให้แสดงผลได้ดีในทุกอุปกรณ์ ตั้งแต่ mobile, tablet, ไปจนถึง desktop

### แนวคิดพื้นฐาน: ปัญหาของรูปภาพแบบเดิม

```css
/* ❌ ปัญหาของรูปภาพแบบเดิม */
.old-image {
  /* รูปภาพมีขนาดคงที่ */
  width: 800px;
  height: 600px;

  /* ปัญหา: */
  /* 1. เกินขนาดหน้าจอ mobile */
  /* 2. ไม่ปรับตัวตาม container */
  /* 3. สร้าง horizontal scrollbar */
  /* 4. UX ไม่ดีใน mobile */
}

/* ✅ วิธีแก้ไขด้วย max-width: 100% */
.responsive-image {
  max-width: 100%;
  height: auto;

  /* ผลลัพธ์: */
  /* 1. ไม่เกินขนาด container */
  /* 2. รักษาสัดส่วนเดิม */
  /* 3. ปรับตัวตามหน้าจอ */
  /* 4. ทำงานได้ทุกอุปกรณ์ */
}

/* HTML Usage */
/*
<img src="image.jpg" alt="Description" class="responsive-image">
*/
```

## 1. max-width: 100% - เทคนิคพื้นฐาน

### การทำงานของ max-width: 100%

```css
/* เข้าใจการทำงานของ max-width: 100% */
.understanding-max-width {
  /* รูปภาพขนาดเล็กกว่า container */
  .small-image {
    /* รูป 400px, container 800px */
    max-width: 100%; /* รูปแสดงขนาด 400px (ขนาดจริง) */
    height: auto;
  }

  /* รูปภาพขนาดใหญ่กว่า container */
  .large-image {
    /* รูป 1200px, container 800px */
    max-width: 100%; /* รูปแสดงขนาด 800px (ปรับลง) */
    height: auto;
  }

  /* การเปรียบเทียบ width vs max-width */
  .width-comparison {
    /* width: 100% - บังคับให้เต็ม container เสมอ */
    .forced-width {
      width: 100%;
      height: auto;
      /* รูปเล็กจะถูกขยายให้เต็ม container (อาจเบลอ) */
    }

    /* max-width: 100% - จำกัดไม่ให้เกิน container */
    .limited-width {
      max-width: 100%;
      height: auto;
      /* รูปเล็กยังคงขนาดเดิม, รูปใหญ่ปรับลง */
    }
  }
}

/* ตัวอย่างการใช้งานพื้นฐาน */
.basic-responsive-images {
  /* Base responsive image class */
  .img-responsive {
    max-width: 100%;
    height: auto;
    display: block; /* ป้องกัน spacing issues */
  }

  /* การใช้กับ different containers */
  .container-small {
    width: 300px;
    padding: 1rem;
    border: 2px solid #e5e7eb;
    margin-bottom: 1rem;
  }

  .container-medium {
    width: 600px;
    padding: 1rem;
    border: 2px solid #3b82f6;
    margin-bottom: 1rem;
  }

  .container-large {
    width: 900px;
    padding: 1rem;
    border: 2px solid #10b981;
    margin-bottom: 1rem;
  }

  /* รูปภาพจะปรับขนาดตาม container อัตโนมัติ */
  .container-small .img-responsive,
  .container-medium .img-responsive,
  .container-large .img-responsive {
    max-width: 100%;
    height: auto;
  }
}
```

### การจัดการ Aspect Ratio

```css
/* การรักษาสัดส่วนของรูปภาพ */
.aspect-ratio-management {
  /* height: auto สำคัญมาก! */
  .correct-aspect {
    max-width: 100%;
    height: auto; /* รักษาสัดส่วนเดิม */
  }

  /* ❌ ผิด: กำหนด height แบบ fixed */
  .wrong-aspect {
    max-width: 100%;
    height: 200px; /* ทำให้รูปผิดสัดส่วน */
  }

  /* การใช้ aspect-ratio property (modern) */
  .modern-aspect {
    max-width: 100%;
    height: auto;
    aspect-ratio: 16 / 9; /* กำหนดสัดส่วน */
    object-fit: cover; /* ครอบรูปให้พอดี */
  }

  /* สัดส่วนต่างๆ ที่ใช้บ่อย */
  .aspect-16-9 {
    aspect-ratio: 16 / 9; /* วิดีโอ/ภาพยนตร์ */
  }

  .aspect-4-3 {
    aspect-ratio: 4 / 3; /* ภาพถ่ายแบบเดิม */
  }

  .aspect-1-1 {
    aspect-ratio: 1 / 1; /* สี่เหลี่ยมจัตุรัส */
  }

  .aspect-3-2 {
    aspect-ratio: 3 / 2; /* ภาพถ่ายดิจิตอล */
  }

  /* Fallback สำหรับ browsers เก่า */
  .aspect-container {
    position: relative;
    width: 100%;
    overflow: hidden;
  }

  /* Padding-bottom trick สำหรับ 16:9 */
  .aspect-16-9-fallback {
    padding-bottom: 56.25%; /* (9/16) * 100% */
  }

  .aspect-container img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
```

## 2. Responsive Images ใน Different Contexts

### Images ใน Flexbox

```css
/* Responsive images ใน flexbox container */
.images-in-flexbox {
  /* Flex container */
  .flex-gallery {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    padding: 1rem;
  }

  /* Flex items with images */
  .flex-item {
    flex: 1 1 calc(33.333% - 1rem); /* 3 columns */
    min-width: 250px; /* minimum width */
  }

  .flex-item img {
    max-width: 100%;
    height: auto;
    display: block;
    border-radius: 0.5rem;
  }

  /* Responsive flex gallery */
  @media (max-width: 768px) {
    .flex-item {
      flex: 1 1 calc(50% - 0.5rem); /* 2 columns */
    }
  }

  @media (max-width: 480px) {
    .flex-item {
      flex: 1 1 100%; /* 1 column */
    }
  }

  /* Equal height flex items */
  .flex-gallery-equal {
    display: flex;
    gap: 1rem;
    align-items: stretch;
  }

  .flex-item-equal {
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  .flex-item-equal img {
    max-width: 100%;
    height: 200px; /* Fixed height */
    object-fit: cover; /* Crop to fit */
    border-radius: 0.5rem;
  }

  .flex-item-equal .content {
    flex: 1;
    padding: 1rem;
    background: white;
    border-radius: 0 0 0.5rem 0.5rem;
  }
}
```

### Images ใน CSS Grid

```css
/* Responsive images ใน grid container */
.images-in-grid {
  /* Grid gallery */
  .grid-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;
    padding: 2rem;
  }

  .grid-item img {
    max-width: 100%;
    height: auto;
    display: block;
    border-radius: 0.5rem;
    transition: transform 0.3s ease;
  }

  .grid-item img:hover {
    transform: scale(1.05);
  }

  /* Grid with fixed aspect ratio */
  .grid-gallery-fixed {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 1rem;
    padding: 1rem;
  }

  .grid-item-fixed {
    background: white;
    border-radius: 0.5rem;
    overflow: hidden;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .grid-item-fixed img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    display: block;
  }

  .grid-item-fixed .content {
    padding: 1rem;
  }

  /* Masonry-like grid */
  .masonry-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    grid-auto-rows: 10px; /* Small row size */
    gap: 1rem;
    padding: 1rem;
  }

  .masonry-item img {
    max-width: 100%;
    height: auto;
    border-radius: 0.5rem;
  }

  /* Different span heights for masonry effect */
  .masonry-item.small {
    grid-row: span 20;
  }

  .masonry-item.medium {
    grid-row: span 30;
  }

  .masonry-item.large {
    grid-row: span 40;
  }
}
```

### Images ใน Cards

```css
/* Responsive images ใน card layouts */
.images-in-cards {
  /* Basic card with image */
  .card {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15);
  }

  .card-image {
    max-width: 100%;
    height: auto;
    display: block;
  }

  .card-content {
    padding: 1.5rem;
  }

  /* Card with fixed image height */
  .card-fixed-height .card-image {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }

  /* Horizontal card layout */
  .card-horizontal {
    display: flex;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    overflow: hidden;
  }

  .card-horizontal .card-image {
    flex: 0 0 40%; /* 40% width */
    max-width: 40%;
    height: auto;
    object-fit: cover;
  }

  .card-horizontal .card-content {
    flex: 1;
    padding: 1.5rem;
  }

  /* Responsive horizontal card */
  @media (max-width: 768px) {
    .card-horizontal {
      flex-direction: column;
    }

    .card-horizontal .card-image {
      flex: none;
      max-width: 100%;
      height: 200px;
    }
  }

  /* Card grid container */
  .cards-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  /* Profile card */
  .profile-card {
    text-align: center;
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .profile-card .avatar {
    width: 100px;
    height: 100px;
    max-width: 100%;
    border-radius: 50%;
    object-fit: cover;
    margin: 0 auto 1rem;
    display: block;
  }
}
```

## 3. Advanced Responsive Image Techniques

### Object-fit และ Object-position

```css
/* การใช้ object-fit กับ responsive images */
.object-fit-techniques {
  /* Container สำหรับทดสอบ */
  .image-container {
    width: 300px;
    height: 200px;
    border: 2px solid #e5e7eb;
    margin: 1rem;
    overflow: hidden;
    border-radius: 0.5rem;
  }

  /* object-fit values */
  .object-fill {
    width: 100%;
    height: 100%;
    object-fit: fill; /* เต็มพื้นที่ (อาจผิดสัดส่วน) */
  }

  .object-contain {
    width: 100%;
    height: 100%;
    object-fit: contain; /* พอดีใน container (อาจมีพื้นที่ว่าง) */
    background: #f3f4f6; /* แสดงพื้นที่ว่าง */
  }

  .object-cover {
    width: 100%;
    height: 100%;
    object-fit: cover; /* ครอบคลุม container (อาจถูกครอบ) */
  }

  .object-none {
    width: 100%;
    height: 100%;
    object-fit: none; /* ขนาดเดิม (อาจถูกครอบ) */
  }

  .object-scale-down {
    width: 100%;
    height: 100%;
    object-fit: scale-down; /* เล็กสุดระหว่าง none และ contain */
  }

  /* object-position สำหรับ object-fit: cover */
  .object-position-demo {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }

  .position-center {
    object-position: center; /* ตรงกลาง (default) */
  }

  .position-top {
    object-position: top; /* ด้านบน */
  }

  .position-bottom {
    object-position: bottom; /* ด้านล่าง */
  }

  .position-left {
    object-position: left; /* ด้านซ้าย */
  }

  .position-right {
    object-position: right; /* ด้านขวา */
  }

  .position-custom {
    object-position: 30% 70%; /* ตำแหน่งเฉพาะ */
  }

  /* Responsive object-fit */
  .responsive-object-fit {
    max-width: 100%;
    height: 250px;
    object-fit: cover;
    object-position: center;
    border-radius: 0.5rem;
  }

  @media (max-width: 768px) {
    .responsive-object-fit {
      height: 200px;
      object-position: top; /* เน้นด้านบนใน mobile */
    }
  }

  @media (max-width: 480px) {
    .responsive-object-fit {
      height: 150px;
    }
  }
}
```

### Background Images แบบ Responsive

```css
/* Responsive background images */
.responsive-backgrounds {
  /* Basic responsive background */
  .bg-responsive {
    background-image: url('image.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    min-height: 300px;
    border-radius: 0.5rem;
  }

  /* Different background-size values */
  .bg-cover {
    background-size: cover; /* ครอบคลุมพื้นที่ */
    background-position: center;
  }

  .bg-contain {
    background-size: contain; /* พอดีในพื้นที่ */
    background-position: center;
    background-color: #f3f4f6; /* สีพื้นหลัง */
  }

  .bg-100-percent {
    background-size: 100% 100%; /* เต็มพื้นที่ (อาจผิดสัดส่วน) */
  }

  .bg-auto {
    background-size: auto; /* ขนาดเดิม */
    background-position: center;
  }

  /* Responsive background positions */
  .bg-mobile-friendly {
    background-image: url('hero-desktop.jpg');
    background-size: cover;
    background-position: center;
    min-height: 400px;
  }

  @media (max-width: 768px) {
    .bg-mobile-friendly {
      background-image: url('hero-mobile.jpg');
      background-position: top;
      min-height: 300px;
    }
  }

  /* Hero section with responsive background */
  .hero-section {
    background-image: url('hero-bg.jpg');
    background-size: cover;
    background-position: center;
    background-attachment: fixed; /* Parallax effect */
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    text-align: center;
  }

  @media (max-width: 768px) {
    .hero-section {
      background-attachment: scroll; /* ปิด parallax ใน mobile */
      min-height: 60vh;
    }
  }

  /* Multiple background images */
  .multiple-backgrounds {
    background-image: url('overlay.png'), url('main-bg.jpg');
    background-size: cover, cover;
    background-position: center, center;
    background-repeat: no-repeat, no-repeat;
    min-height: 300px;
  }

  /* Gradient overlay on background */
  .bg-with-overlay {
    background-image: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
      url('background.jpg');
    background-size: cover;
    background-position: center;
    color: white;
    min-height: 300px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
```

## 4. Performance Optimization

### Lazy Loading

```css
/* Styles สำหรับ lazy loading */
.lazy-loading {
  /* Image placeholder */
  .img-placeholder {
    background: #f3f4f6;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #9ca3af;
    font-size: 0.875rem;
    border-radius: 0.5rem;
  }

  /* Loading state */
  .img-loading {
    max-width: 100%;
    height: auto;
    opacity: 0.5;
    transition: opacity 0.3s ease;
  }

  /* Loaded state */
  .img-loaded {
    max-width: 100%;
    height: auto;
    opacity: 1;
    transition: opacity 0.3s ease;
  }

  /* Blur-up technique */
  .img-blur-up {
    max-width: 100%;
    height: auto;
    filter: blur(10px);
    transition: filter 0.3s ease;
  }

  .img-blur-up.loaded {
    filter: blur(0);
  }

  /* Progressive loading container */
  .progressive-image {
    position: relative;
    overflow: hidden;
    border-radius: 0.5rem;
  }

  .progressive-image .img-small {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: blur(5px);
    transition: opacity 0.3s ease;
  }

  .progressive-image .img-large {
    max-width: 100%;
    height: auto;
    opacity: 0;
    transition: opacity 0.3s ease;
  }

  .progressive-image .img-large.loaded {
    opacity: 1;
  }

  .progressive-image .img-large.loaded + .img-small {
    opacity: 0;
  }
}

/* HTML Example for Progressive Loading */
/*
<div class="progressive-image">
  <img src="image-large.jpg" alt="Description" class="img-large" loading="lazy">
  <img src="image-small.jpg" alt="" class="img-small">
</div>
*/
```

### Responsive Image Loading

```css
/* Optimized responsive images */
.optimized-responsive {
  /* Base responsive image */
  .img-optimized {
    max-width: 100%;
    height: auto;
    display: block;

    /* Performance hints */
    content-visibility: auto;
    contain-intrinsic-size: 300px 200px;

    /* Loading optimization */
    loading: lazy;
    decoding: async;
  }

  /* Critical images (above the fold) */
  .img-critical {
    max-width: 100%;
    height: auto;
    display: block;

    /* Load immediately */
    loading: eager;
    fetchpriority: high;
  }

  /* Container with size hints */
  .image-container-optimized {
    /* Prevent layout shift */
    aspect-ratio: 16 / 9;
    overflow: hidden;
    border-radius: 0.5rem;
    background: #f3f4f6;
  }

  .image-container-optimized img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
  }

  .image-container-optimized:hover img {
    transform: scale(1.05);
  }

  /* Skeleton loading */
  .skeleton-image {
    background: linear-gradient(90deg, #f0f0f0 25%, #e0e0e0 50%, #f0f0f0 75%);
    background-size: 200% 100%;
    animation: skeleton-loading 1.5s infinite;
    border-radius: 0.5rem;
  }

  @keyframes skeleton-loading {
    0% {
      background-position: 200% 0;
    }
    100% {
      background-position: -200% 0;
    }
  }

  /* Error state */
  .img-error {
    max-width: 100%;
    height: 200px;
    background: #fee2e2;
    border: 2px dashed #fca5a5;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #dc2626;
    font-size: 0.875rem;
    border-radius: 0.5rem;
  }

  .img-error::before {
    content: '🖼️ Image failed to load';
  }
}
```

## 5. Common Patterns และ Use Cases

### Image Galleries

```css
/* Responsive image galleries */
.responsive-galleries {
  /* Simple grid gallery */
  .gallery-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1rem;
    padding: 1rem;
  }

  .gallery-item {
    position: relative;
    overflow: hidden;
    border-radius: 0.5rem;
    aspect-ratio: 1;
    background: #f3f4f6;
  }

  .gallery-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
    cursor: pointer;
  }

  .gallery-item:hover img {
    transform: scale(1.1);
  }

  /* Overlay on hover */
  .gallery-item .overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.5);
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 0.3s ease;
  }

  .gallery-item:hover .overlay {
    opacity: 1;
  }

  /* Responsive gallery sizes */
  @media (max-width: 768px) {
    .gallery-grid {
      grid-template-columns: repeat(2, 1fr);
      gap: 0.5rem;
      padding: 0.5rem;
    }
  }

  @media (max-width: 480px) {
    .gallery-grid {
      grid-template-columns: 1fr;
    }
  }

  /* Featured gallery with different sizes */
  .featured-gallery {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(3, 200px);
    gap: 1rem;
    padding: 1rem;
  }

  .featured-item {
    position: relative;
    overflow: hidden;
    border-radius: 0.5rem;
  }

  .featured-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* Feature item spans */
  .featured-item.large {
    grid-column: span 2;
    grid-row: span 2;
  }

  .featured-item.wide {
    grid-column: span 2;
  }

  .featured-item.tall {
    grid-row: span 2;
  }

  /* Mobile responsive for featured gallery */
  @media (max-width: 768px) {
    .featured-gallery {
      grid-template-columns: repeat(2, 1fr);
      grid-template-rows: repeat(auto, 150px);
    }

    .featured-item.large,
    .featured-item.wide,
    .featured-item.tall {
      grid-column: span 1;
      grid-row: span 1;
    }
  }
}
```

### Hero Sections

```css
/* Responsive hero sections with images */
.hero-sections {
  /* Image-based hero */
  .hero-image {
    position: relative;
    height: 100vh;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .hero-image img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: -1;
  }

  .hero-content {
    text-align: center;
    color: white;
    max-width: 600px;
    padding: 2rem;
    background: rgba(0, 0, 0, 0.3);
    border-radius: 0.5rem;
    backdrop-filter: blur(10px);
  }

  .hero-title {
    font-size: clamp(2rem, 5vw, 4rem);
    font-weight: bold;
    margin-bottom: 1rem;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  }

  .hero-description {
    font-size: clamp(1rem, 2vw, 1.25rem);
    margin-bottom: 2rem;
    text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
  }

  /* Split hero (image + content) */
  .hero-split {
    display: grid;
    grid-template-columns: 1fr 1fr;
    min-height: 100vh;
    align-items: center;
  }

  .hero-split .hero-image-container {
    position: relative;
    height: 100%;
    overflow: hidden;
  }

  .hero-split .hero-image-container img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .hero-split .hero-content {
    padding: 4rem;
    background: white;
    color: #1f2937;
  }

  /* Responsive hero */
  @media (max-width: 768px) {
    .hero-image {
      height: 70vh;
    }

    .hero-split {
      grid-template-columns: 1fr;
      grid-template-rows: 50vh auto;
    }

    .hero-split .hero-content {
      padding: 2rem;
    }
  }

  /* Parallax hero */
  .hero-parallax {
    height: 100vh;
    background-attachment: fixed;
    background-size: cover;
    background-position: center;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  @media (max-width: 768px) {
    .hero-parallax {
      background-attachment: scroll; /* Disable parallax on mobile */
      height: 70vh;
    }
  }
}
```

### Product Images

```css
/* E-commerce product images */
.product-images {
  /* Product card */
  .product-card {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .product-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15);
  }

  .product-image-container {
    position: relative;
    aspect-ratio: 1;
    overflow: hidden;
    background: #f8fafc;
  }

  .product-image {
    width: 100%;
    height: 100%;
    object-fit: contain; /* Show full product */
    padding: 1rem;
    transition: transform 0.3s ease;
  }

  .product-card:hover .product-image {
    transform: scale(1.05);
  }

  /* Product badges */
  .product-badge {
    position: absolute;
    top: 0.5rem;
    left: 0.5rem;
    background: #ef4444;
    color: white;
    padding: 0.25rem 0.5rem;
    border-radius: 0.25rem;
    font-size: 0.75rem;
    font-weight: 600;
    z-index: 1;
  }

  .product-badge.sale {
    background: #ef4444;
  }

  .product-badge.new {
    background: #10b981;
  }

  /* Product gallery */
  .product-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;
    padding: 2rem;
  }

  /* Product grid responsive */
  @media (max-width: 640px) {
    .product-gallery {
      grid-template-columns: repeat(2, 1fr);
      gap: 1rem;
      padding: 1rem;
    }

    .product-image {
      padding: 0.5rem;
    }
  }

  @media (max-width: 480px) {
    .product-gallery {
      grid-template-columns: 1fr;
    }
  }

  /* Product detail page */
  .product-detail {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 3rem;
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem;
  }

  .product-images-main {
    display: grid;
    gap: 1rem;
  }

  .product-main-image {
    aspect-ratio: 1;
    overflow: hidden;
    border-radius: 0.5rem;
    background: #f8fafc;
  }

  .product-main-image img {
    width: 100%;
    height: 100%;
    object-fit: contain;
    padding: 1rem;
  }

  .product-thumbnails {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0.5rem;
  }

  .product-thumbnail {
    aspect-ratio: 1;
    overflow: hidden;
    border-radius: 0.25rem;
    border: 2px solid transparent;
    cursor: pointer;
    background: #f8fafc;
  }

  .product-thumbnail.active {
    border-color: #3b82f6;
  }

  .product-thumbnail img {
    width: 100%;
    height: 100%;
    object-fit: contain;
    padding: 0.25rem;
  }

  /* Mobile product detail */
  @media (max-width: 768px) {
    .product-detail {
      grid-template-columns: 1fr;
      gap: 2rem;
      padding: 1rem;
    }
  }
}
```

## 6. Best Practices และ Tips

### Performance Best Practices

```css
/* Performance optimization */
.performance-tips {
  /* ✅ Always include these properties */
  .optimal-responsive-image {
    max-width: 100%;
    height: auto;
    display: block; /* ป้องกัน inline spacing */

    /* Modern performance hints */
    content-visibility: auto;
    contain-intrinsic-size: 300px 200px;

    /* Loading hints */
    loading: lazy; /* For non-critical images */
    decoding: async;
  }

  /* ✅ Critical images (above the fold) */
  .critical-image {
    max-width: 100%;
    height: auto;
    display: block;

    /* Priority loading */
    loading: eager;
    fetchpriority: high;
  }

  /* ✅ Size hints to prevent layout shift */
  .image-with-dimensions {
    max-width: 100%;
    height: auto;
    aspect-ratio: 16 / 9; /* Maintain aspect ratio */
  }

  /* ✅ Progressive enhancement */
  .progressive-image-loading {
    background: #f3f4f6; /* Placeholder color */
    border-radius: 0.5rem;
    transition: opacity 0.3s ease;
  }

  .progressive-image-loading[data-loaded='false'] {
    opacity: 0.5;
  }

  .progressive-image-loading[data-loaded='true'] {
    opacity: 1;
  }

  /* ❌ Avoid these patterns */
  .avoid-these {
    /* Don't use fixed dimensions without max-width */
    .wrong-fixed {
      width: 800px; /* Will break on mobile */
      height: 600px;
    }

    /* Don't forget height: auto */
    .wrong-height {
      max-width: 100%;
      height: 300px; /* Fixed height breaks aspect ratio */
    }

    /* Don't use width: 100% unnecessarily */
    .wrong-width {
      width: 100%; /* Forces small images to stretch */
      height: auto;
    }
  }
}
```

### Accessibility Considerations

```css
/* Accessibility for responsive images */
.accessibility-images {
  /* Focus states */
  .focusable-image {
    max-width: 100%;
    height: auto;
    border-radius: 0.5rem;
    transition: outline 0.2s ease;
  }

  .focusable-image:focus {
    outline: 2px solid #3b82f6;
    outline-offset: 2px;
  }

  /* High contrast support */
  @media (prefers-contrast: high) {
    .image-container {
      border: 2px solid currentColor;
    }
  }

  /* Reduced motion support */
  @media (prefers-reduced-motion: reduce) {
    .animated-image {
      transition: none;
      transform: none !important;
    }

    .hover-effect:hover {
      transform: none !important;
    }
  }

  /* Dark mode considerations */
  @media (prefers-color-scheme: dark) {
    .image-placeholder {
      background: #374151;
      color: #d1d5db;
    }

    .image-border {
      border-color: #4b5563;
    }
  }

  /* Screen reader support */
  .sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
  }
}
```

### Browser Compatibility

```css
/* Browser compatibility considerations */
.browser-compatibility {
  /* Modern approach with fallbacks */
  .modern-responsive-image {
    max-width: 100%;
    height: auto;

    /* Modern properties with fallbacks */
    aspect-ratio: 16 / 9;
    object-fit: cover;

    /* Fallback for older browsers */
    background: #f3f4f6;
  }

  /* Legacy browser support */
  @supports not (aspect-ratio: 1) {
    .aspect-ratio-fallback {
      position: relative;
      overflow: hidden;
    }

    .aspect-ratio-fallback::before {
      content: '';
      display: block;
      padding-bottom: 56.25%; /* 16:9 ratio */
    }

    .aspect-ratio-fallback img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  /* IE11 compatibility */
  @media screen and (-ms-high-contrast: active), (-ms-high-contrast: none) {
    .ie11-fix img {
      width: auto\9; /* IE11 hack */
      max-width: 100%;
      height: auto;
    }
  }
}
```

## สรุป: Responsive Images Best Practices

### Key Concepts 🎯

1. **พื้นฐาน: max-width: 100%**

   ```css
   .responsive-image {
     max-width: 100%;
     height: auto;
     display: block;
   }
   ```

2. **Aspect Ratio Management**

   - ใช้ `height: auto` เสมอ
   - ใช้ `aspect-ratio` สำหรับ modern browsers
   - ใช้ `object-fit` สำหรับ fixed containers

3. **Performance Optimization**

   - `loading="lazy"` สำหรับ non-critical images
   - `loading="eager"` สำหรับ critical images
   - ใช้ `content-visibility: auto`

4. **Modern Techniques**

   - CSS Grid และ Flexbox
   - `object-fit` และ `object-position`
   - Progressive loading
   - Lazy loading

5. **Accessibility**
   - Alt text ที่มีความหมาย
   - Focus states
   - High contrast support
   - Reduced motion respect

### Quick Reference 📋

```css
/* Essential responsive image */
.img-responsive {
  max-width: 100%;
  height: auto;
  display: block;
}

/* Modern responsive image */
.img-modern {
  max-width: 100%;
  height: auto;
  aspect-ratio: 16 / 9;
  object-fit: cover;
  loading: lazy;
  decoding: async;
}

/* Critical image */
.img-critical {
  max-width: 100%;
  height: auto;
  loading: eager;
  fetchpriority: high;
}
```

Responsive Images ด้วย `max-width: 100%` เป็นเทคนิคพื้นฐานที่สำคัญที่สุดในการสร้าง responsive design ที่ทำงานได้ดีในทุกอุปกรณ์!
