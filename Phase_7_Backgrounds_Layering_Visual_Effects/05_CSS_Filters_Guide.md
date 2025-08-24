# CSS Filters: การใช้ Filter Effects ใน CSS

## ภาพรวม CSS Filters

**CSS Filters** เป็นเครื่องมือที่ทรงพลังในการปรับแต่งรูปลักษณ์ของ elements โดยไม่ต้องแก้ไขไฟล์ต้นฉบับ สามารถสร้างเอฟเฟกต์ภาพที่หลากหลายได้

### Filter Functions พื้นฐาน

```css
/* Filter functions หลัก */
.filter-basics {
  /* Blur - เบลอ */
  .blur-filter {
    filter: blur(5px);
    /* เบลอ 5 พิกเซล */
  }

  /* Brightness - ความสว่าง */
  .brightness-filter {
    filter: brightness(150%);
    /* เพิ่มความสว่าง 150% */
  }

  /* Contrast - ความคมชัด */
  .contrast-filter {
    filter: contrast(200%);
    /* เพิ่มความคมชัด 200% */
  }

  /* Grayscale - สีเทา */
  .grayscale-filter {
    filter: grayscale(100%);
    /* เปลี่ยนเป็นสีเทา 100% */
  }

  /* Saturate - ความอิ่มตัวของสี */
  .saturate-filter {
    filter: saturate(200%);
    /* เพิ่มความอิ่มตัว 200% */
  }

  /* Sepia - โทนสีเซเปีย */
  .sepia-filter {
    filter: sepia(80%);
    /* โทนสีเซเปีย 80% */
  }

  /* Hue-rotate - หมุนสี */
  .hue-rotate-filter {
    filter: hue-rotate(90deg);
    /* หมุนสี 90 องศา */
  }

  /* Invert - กลับสี */
  .invert-filter {
    filter: invert(100%);
    /* กลับสี 100% */
  }

  /* Opacity - ความโปร่งใส */
  .opacity-filter {
    filter: opacity(50%);
    /* ความโปร่งใส 50% */
  }

  /* Drop-shadow - เงา */
  .drop-shadow-filter {
    filter: drop-shadow(4px 4px 8px rgba(0, 0, 0, 0.3));
    /* เงาตก */
  }
}
```

## 1. blur(): การสร้างเอฟเฟกต์เบลอ

### พื้นฐาน blur()

```css
/* Blur filter พื้นฐาน */
.blur-effects {
  /* Basic blur values */
  .blur-light {
    filter: blur(2px);
    /* เบลอเล็กน้อย - เหมาะสำหรับ subtle effects */
  }

  .blur-medium {
    filter: blur(5px);
    /* เบลอปานกลาง - เหมาะสำหรับ backgrounds */
  }

  .blur-heavy {
    filter: blur(10px);
    /* เบลอมาก - เหมาะสำหรับ privacy/loading states */
  }

  .blur-extreme {
    filter: blur(20px);
    /* เบลอมากมาย - เหมาะสำหรับ abstract effects */
  }

  /* Blur with different units */
  .blur-rem {
    filter: blur(0.5rem);
    /* ใช้ rem unit - responsive กับ font-size */
  }

  .blur-em {
    filter: blur(0.3em);
    /* ใช้ em unit - relative กับ element font-size */
  }

  /* Zero blur (no effect) */
  .no-blur {
    filter: blur(0);
    /* ไม่เบลอ - ใช้เพื่อ reset */
  }
}
```

### Practical Blur Applications

```css
/* การใช้งาน blur ในสถานการณ์จริง */
.blur-applications {
  /* Background blur effects */
  .background-blur {
    .backdrop-blur {
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.2);
      border-radius: 12px;
      padding: 24px;
      /* Glassmorphism effect */
    }

    .image-backdrop {
      position: relative;
      overflow: hidden;
    }

    .image-backdrop::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-image: inherit;
      filter: blur(8px);
      z-index: -1;
      transform: scale(1.1);
      /* Background image blur */
    }
  }

  /* Loading states */
  .loading-blur {
    .loading-content {
      filter: blur(3px);
      transition: filter 0.3s ease;
      pointer-events: none;
      /* Content blur during loading */
    }

    .loading-content.loaded {
      filter: blur(0);
      pointer-events: auto;
      /* Remove blur when loaded */
    }

    .skeleton-blur {
      background: linear-gradient(90deg, #f0f0f0, #e0e0e0, #f0f0f0);
      background-size: 200% 100%;
      filter: blur(1px);
      animation: skeletonShimmer 1.5s ease-in-out infinite;
      /* Skeleton loading with subtle blur */
    }

    @keyframes skeletonShimmer {
      0% {
        background-position: -200% 0;
      }
      100% {
        background-position: 200% 0;
      }
    }
  }

  /* Focus and interaction states */
  .interactive-blur {
    .focus-blur {
      transition: filter 0.3s ease;
    }

    .focus-blur:not(:focus) {
      filter: blur(2px);
      /* Blur when not focused */
    }

    .focus-blur:focus {
      filter: blur(0);
      /* Sharp when focused */
    }

    .hover-deblur {
      filter: blur(4px);
      transition: filter 0.3s ease;
    }

    .hover-deblur:hover {
      filter: blur(0);
      /* Remove blur on hover */
    }

    .active-blur {
      transition: filter 0.1s ease;
    }

    .active-blur:active {
      filter: blur(1px);
      /* Slight blur when pressed */
    }
  }

  /* Privacy and censoring */
  .privacy-blur {
    .censored-content {
      filter: blur(8px);
      transition: filter 0.3s ease;
      cursor: pointer;
      position: relative;
    }

    .censored-content::after {
      content: 'Click to reveal';
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: rgba(0, 0, 0, 0.7);
      color: white;
      padding: 8px 16px;
      border-radius: 4px;
      font-size: 14px;
    }

    .censored-content.revealed {
      filter: blur(0);
    }

    .censored-content.revealed::after {
      display: none;
    }

    .sensitive-blur {
      filter: blur(15px);
      /* Heavy blur for sensitive content */
    }
  }

  /* Image gallery effects */
  .gallery-blur {
    .gallery-item {
      transition: filter 0.3s ease, transform 0.3s ease;
      filter: blur(2px);
      transform: scale(0.95);
    }

    .gallery-item:hover,
    .gallery-item.active {
      filter: blur(0);
      transform: scale(1);
      /* Focus on active/hovered item */
    }

    .gallery-container:hover .gallery-item:not(:hover) {
      filter: blur(5px);
      opacity: 0.7;
      /* Blur non-hovered items in container */
    }
  }
}
```

### Advanced Blur Techniques

```css
/* เทคนิค blur ขั้นสูง */
.advanced-blur {
  /* Animated blur effects */
  .animated-blur {
    .pulse-blur {
      animation: pulseBlur 2s ease-in-out infinite;
    }

    @keyframes pulseBlur {
      0%,
      100% {
        filter: blur(0);
      }
      50% {
        filter: blur(5px);
      }
    }

    .wave-blur {
      animation: waveBlur 3s ease-in-out infinite;
    }

    @keyframes waveBlur {
      0%,
      100% {
        filter: blur(0) hue-rotate(0deg);
      }
      25% {
        filter: blur(3px) hue-rotate(90deg);
      }
      50% {
        filter: blur(6px) hue-rotate(180deg);
      }
      75% {
        filter: blur(3px) hue-rotate(270deg);
      }
    }

    .breathing-blur {
      animation: breathingBlur 4s ease-in-out infinite;
    }

    @keyframes breathingBlur {
      0%,
      100% {
        filter: blur(1px) scale(1);
      }
      50% {
        filter: blur(4px) scale(1.02);
      }
    }
  }

  /* Directional blur simulation */
  .directional-blur {
    .motion-blur-horizontal {
      filter: blur(0 3px);
      /* Horizontal motion blur (not standard, but conceptual) */
      /* Alternative: use multiple shadows */
      box-shadow: 1px 0 0 rgba(0, 0, 0, 0.1), 2px 0 0 rgba(0, 0, 0, 0.08),
        3px 0 0 rgba(0, 0, 0, 0.06), 4px 0 0 rgba(0, 0, 0, 0.04),
        5px 0 0 rgba(0, 0, 0, 0.02);
    }

    .motion-blur-vertical {
      /* Vertical motion blur simulation */
      box-shadow: 0 1px 0 rgba(0, 0, 0, 0.1), 0 2px 0 rgba(0, 0, 0, 0.08),
        0 3px 0 rgba(0, 0, 0, 0.06), 0 4px 0 rgba(0, 0, 0, 0.04),
        0 5px 0 rgba(0, 0, 0, 0.02);
    }
  }

  /* Responsive blur */
  .responsive-blur {
    /* Mobile: lighter blur for performance */
    filter: blur(2px);
  }

  @media (min-width: 768px) {
    .responsive-blur {
      /* Desktop: heavier blur when hardware can handle */
      filter: blur(5px);
    }
  }

  @media (prefers-reduced-motion: reduce) {
    .responsive-blur {
      /* Respect motion preferences */
      filter: blur(3px);
      animation: none;
    }
  }

  /* Performance-optimized blur */
  .optimized-blur {
    .gpu-blur {
      filter: blur(5px);
      transform: translateZ(0);
      will-change: filter;
      /* Force GPU acceleration */
    }

    .contained-blur {
      filter: blur(3px);
      contain: layout style paint;
      /* Contain repaints */
    }
  }
}
```

## 2. brightness(): การปรับความสว่าง

### พื้นฐาน brightness()

```css
/* Brightness filter พื้นฐาน */
.brightness-effects {
  /* Basic brightness values */
  .brightness-dark {
    filter: brightness(50%);
    /* ลดความสว่าง 50% - ทำให้มืดขึ้น */
  }

  .brightness-normal {
    filter: brightness(100%);
    /* ความสว่างปกติ (default) */
  }

  .brightness-bright {
    filter: brightness(150%);
    /* เพิ่มความสว่าง 150% - ทำให้สว่างขึ้น */
  }

  .brightness-very-bright {
    filter: brightness(200%);
    /* เพิ่มความสว่างมาก 200% */
  }

  .brightness-overexposed {
    filter: brightness(300%);
    /* เพิ่มความสว่างมากมาย - overexposed effect */
  }

  /* Decimal values */
  .brightness-decimal {
    filter: brightness(0.8);
    /* ใช้ decimal แทน percentage */
  }

  /* Zero brightness (black) */
  .brightness-black {
    filter: brightness(0%);
    /* ความสว่าง 0% = สีดำ */
  }

  /* Combined with other values */
  .brightness-range {
    .very-dark {
      filter: brightness(20%);
    }
    .dark {
      filter: brightness(60%);
    }
    .slightly-dark {
      filter: brightness(80%);
    }
    .normal {
      filter: brightness(100%);
    }
    .slightly-bright {
      filter: brightness(120%);
    }
    .bright {
      filter: brightness(160%);
    }
    .very-bright {
      filter: brightness(220%);
    }
  }
}
```

### Practical Brightness Applications

```css
/* การใช้งาน brightness ในสถานการณ์จริง */
.brightness-applications {
  /* Image overlay effects */
  .image-overlays {
    .darkened-overlay {
      position: relative;
      overflow: hidden;
    }

    .darkened-overlay img {
      filter: brightness(70%);
      transition: filter 0.3s ease;
    }

    .darkened-overlay:hover img {
      filter: brightness(100%);
      /* Brighten on hover */
    }

    .brightened-text-bg {
      position: relative;
    }

    .brightened-text-bg::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: inherit;
      filter: brightness(300%);
      z-index: -1;
      /* Bright background for text overlay */
    }
  }

  /* Button states */
  .button-brightness {
    .btn-brightness {
      background: #3b82f6;
      color: white;
      border: none;
      padding: 12px 24px;
      border-radius: 6px;
      cursor: pointer;
      transition: filter 0.2s ease;
    }

    .btn-brightness:hover {
      filter: brightness(110%);
      /* Slightly brighter on hover */
    }

    .btn-brightness:active {
      filter: brightness(90%);
      /* Darker when pressed */
    }

    .btn-brightness:disabled {
      filter: brightness(60%);
      opacity: 0.7;
      cursor: not-allowed;
      /* Dimmed when disabled */
    }
  }

  /* Theme switching */
  .theme-brightness {
    .dark-mode-image {
      filter: brightness(80%) contrast(120%);
      /* Adjust for dark theme */
    }

    .light-mode-image {
      filter: brightness(100%) contrast(100%);
      /* Normal for light theme */
    }

    [data-theme='dark'] .theme-adaptive {
      filter: brightness(85%);
      /* Reduce brightness in dark mode */
    }

    [data-theme='light'] .theme-adaptive {
      filter: brightness(100%);
      /* Normal brightness in light mode */
    }
  }

  /* Loading and progress states */
  .loading-brightness {
    .loading-dim {
      filter: brightness(50%);
      transition: filter 0.3s ease;
      /* Dim during loading */
    }

    .loading-dim.loaded {
      filter: brightness(100%);
      /* Return to normal when loaded */
    }

    .progress-brighten {
      filter: brightness(70%);
      transition: filter 0.5s ease;
    }

    .progress-brighten[data-progress='complete'] {
      filter: brightness(120%);
      /* Brighten when complete */
    }
  }

  /* Error and success states */
  .state-brightness {
    .error-state {
      filter: brightness(80%) saturate(150%) hue-rotate(-10deg);
      /* Slightly dark with red tint for errors */
    }

    .success-state {
      filter: brightness(110%) saturate(120%) hue-rotate(10deg);
      /* Slightly bright with green tint for success */
    }

    .warning-state {
      filter: brightness(130%) saturate(150%) sepia(20%);
      /* Bright with yellow tint for warnings */
    }
  }
}
```

### Advanced Brightness Techniques

```css
/* เทคนิค brightness ขั้นสูง */
.advanced-brightness {
  /* Animated brightness effects */
  .animated-brightness {
    .pulse-brightness {
      animation: pulseBright 2s ease-in-out infinite;
    }

    @keyframes pulseBright {
      0%,
      100% {
        filter: brightness(100%);
      }
      50% {
        filter: brightness(130%);
      }
    }

    .flash-effect {
      animation: flashBright 0.1s ease-in-out;
    }

    @keyframes flashBright {
      0% {
        filter: brightness(100%);
      }
      50% {
        filter: brightness(300%);
      }
      100% {
        filter: brightness(100%);
      }
    }

    .sunrise-effect {
      animation: sunrise 10s ease-in-out infinite;
    }

    @keyframes sunrise {
      0% {
        filter: brightness(20%);
      }
      25% {
        filter: brightness(60%);
      }
      50% {
        filter: brightness(100%);
      }
      75% {
        filter: brightness(120%);
      }
      100% {
        filter: brightness(20%);
      }
    }
  }

  /* Interactive brightness */
  .interactive-brightness {
    .brightness-slider {
      transition: filter 0.1s ease;
    }

    .brightness-slider[data-brightness='0'] {
      filter: brightness(0%);
    }
    .brightness-slider[data-brightness='25'] {
      filter: brightness(25%);
    }
    .brightness-slider[data-brightness='50'] {
      filter: brightness(50%);
    }
    .brightness-slider[data-brightness='75'] {
      filter: brightness(75%);
    }
    .brightness-slider[data-brightness='100'] {
      filter: brightness(100%);
    }
    .brightness-slider[data-brightness='125'] {
      filter: brightness(125%);
    }
    .brightness-slider[data-brightness='150'] {
      filter: brightness(150%);
    }

    .proximity-brightness {
      transition: filter 0.3s ease;
      filter: brightness(70%);
    }

    .proximity-brightness:hover {
      filter: brightness(100%);
    }

    /* Brightness based on scroll position */
    .scroll-brightness {
      transition: filter 0.3s ease;
    }

    .scroll-brightness.in-viewport {
      filter: brightness(120%);
    }

    .scroll-brightness.out-viewport {
      filter: brightness(80%);
    }
  }

  /* Conditional brightness */
  .conditional-brightness {
    /* Time-based brightness */
    .time-adaptive {
      filter: brightness(100%);
    }

    @media (prefers-color-scheme: dark) {
      .time-adaptive {
        filter: brightness(85%);
        /* Reduce brightness in dark mode */
      }
    }

    /* Battery-saving mode */
    .battery-save {
      filter: brightness(90%);
      /* Slightly reduce brightness to save battery */
    }

    /* High contrast mode */
    @media (prefers-contrast: high) {
      .contrast-adaptive {
        filter: brightness(120%) contrast(150%);
        /* Increase brightness and contrast */
      }
    }
  }

  /* Performance optimization */
  .optimized-brightness {
    .efficient-brightness {
      filter: brightness(110%);
      contain: style layout paint;
      /* Optimize repaints */
    }

    .hardware-accelerated {
      filter: brightness(120%);
      transform: translateZ(0);
      will-change: filter;
      /* Use GPU acceleration */
    }
  }
}
```

## 3. การรวม Filter Functions

### Combining Multiple Filters

```css
/* การรวม filter functions หลายตัว */
.combined-filters {
  /* Basic combinations */
  .blur-bright {
    filter: blur(3px) brightness(120%);
    /* เบลอ + เพิ่มความสว่าง */
  }

  .vintage-effect {
    filter: sepia(60%) contrast(110%) brightness(90%) saturate(130%);
    /* เอฟเฟกต์ภาพโบราณ */
  }

  .modern-photo {
    filter: contrast(120%) brightness(105%) saturate(110%) blur(0.5px);
    /* เอฟเฟกต์ภาพสมัยใหม่ */
  }

  .dramatic-effect {
    filter: contrast(150%) brightness(80%) saturate(200%) blur(1px);
    /* เอฟเฟกต์ดราม่า */
  }

  /* Instagram-style filters */
  .instagram-filters {
    .clarendon {
      filter: contrast(120%) saturate(125%) brightness(110%);
    }

    .gingham {
      filter: brightness(105%) hue-rotate(-10deg) contrast(110%);
    }

    .moon {
      filter: grayscale(100%) contrast(110%) brightness(110%);
    }

    .lark {
      filter: contrast(90%) saturate(110%) brightness(110%) sepia(15%);
    }

    .reyes {
      filter: sepia(22%) brightness(110%) contrast(85%) saturate(75%);
    }

    .juno {
      filter: sepia(35%) contrast(115%) brightness(115%) saturate(180%);
    }

    .slumber {
      filter: saturate(66%) brightness(105%) sepia(35%);
    }

    .crema {
      filter: sepia(50%) contrast(125%) brightness(115%) saturate(90%)
        hue-rotate(-2deg);
    }

    .ludwig {
      filter: sepia(25%) contrast(105%) brightness(103%) saturate(200%);
    }

    .aden {
      filter: hue-rotate(-20deg) contrast(90%) saturate(85%) brightness(120%);
    }
  }

  /* Artistic effects */
  .artistic-effects {
    .oil-painting {
      filter: contrast(130%) saturate(150%) blur(1.5px) brightness(105%);
      /* เอฟเฟกต์ภาพวาดสีน้ำมัน */
    }

    .watercolor {
      filter: blur(2px) brightness(115%) contrast(85%) saturate(120%);
      /* เอฟเฟกต์สีน้ำ */
    }

    .sketch {
      filter: grayscale(100%) contrast(200%) brightness(150%) invert(100%);
      /* เอฟเฟกต์ภาพร่าง */
    }

    .neon-glow {
      filter: brightness(200%) contrast(150%) saturate(300%) blur(1px);
      /* เอฟเฟกต์เรืองแสงนีออน */
    }

    .cyberpunk {
      filter: contrast(150%) brightness(110%) saturate(200%) hue-rotate(270deg)
        blur(0.5px);
      /* เอฟเฟกต์ไซเบอร์พังค์ */
    }
  }

  /* Weather and time effects */
  .atmospheric-effects {
    .foggy-morning {
      filter: brightness(90%) contrast(80%) blur(2px) sepia(10%);
      /* เอฟเฟกต์หมอกยามเช้า */
    }

    .sunny-day {
      filter: brightness(120%) contrast(110%) saturate(130%) blur(0.3px);
      /* เอฟเฟกต์วันแดดสดใส */
    }

    .rainy-day {
      filter: brightness(70%) contrast(90%) saturate(80%) blur(1px);
      /* เอฟเฟกต์วันฝนตก */
    }

    .golden-hour {
      filter: brightness(115%) contrast(105%) saturate(140%) sepia(15%)
        hue-rotate(5deg);
      /* เอฟเฟกต์ golden hour */
    }

    .blue-hour {
      filter: brightness(85%) contrast(115%) saturate(120%) hue-rotate(10deg)
        blur(0.5px);
      /* เอฟเฟกต์ blue hour */
    }
  }
}
```

### Interactive Filter Combinations

```css
/* การรวม filters แบบ interactive */
.interactive-combinations {
  /* Hover effect combinations */
  .hover-combinations {
    .photo-hover {
      filter: grayscale(100%) brightness(80%);
      transition: filter 0.5s ease;
    }

    .photo-hover:hover {
      filter: grayscale(0%) brightness(110%) contrast(120%) saturate(130%);
      /* ภาพขาวดำเป็นสี + เพิ่มความสวยงาม */
    }

    .blur-focus {
      filter: blur(5px) brightness(70%);
      transition: filter 0.4s ease;
    }

    .blur-focus:hover {
      filter: blur(0) brightness(100%) contrast(110%);
      /* จากเบลอมืดเป็นชัดสว่าง */
    }

    .vintage-modern {
      filter: sepia(80%) contrast(90%) brightness(80%);
      transition: filter 0.6s ease;
    }

    .vintage-modern:hover {
      filter: sepia(0%) contrast(120%) brightness(110%) saturate(120%);
      /* จาก vintage เป็น modern */
    }
  }

  /* Focus state combinations */
  .focus-combinations {
    .form-focus {
      filter: brightness(95%) contrast(90%);
      transition: filter 0.3s ease;
    }

    .form-focus:focus {
      filter: brightness(105%) contrast(110%) blur(0) saturate(110%);
      /* เพิ่มความชัดเจนเมื่อ focus */
    }

    .button-focus {
      filter: brightness(100%);
      transition: filter 0.2s ease;
    }

    .button-focus:focus {
      filter: brightness(115%) contrast(110%) drop-shadow(0 0 8px rgba(59, 130, 246, 0.4));
      /* เพิ่มความสว่างและเงาเมื่อ focus */
    }
  }

  /* Animation combinations */
  .animated-combinations {
    .breathing-effect {
      animation: breathingFilters 4s ease-in-out infinite;
    }

    @keyframes breathingFilters {
      0%,
      100% {
        filter: brightness(100%) contrast(100%) blur(0);
      }
      50% {
        filter: brightness(110%) contrast(110%) blur(1px);
      }
    }

    .color-shift {
      animation: colorShiftFilters 6s ease-in-out infinite;
    }

    @keyframes colorShiftFilters {
      0% {
        filter: hue-rotate(0deg) brightness(100%) saturate(100%);
      }
      25% {
        filter: hue-rotate(90deg) brightness(110%) saturate(130%);
      }
      50% {
        filter: hue-rotate(180deg) brightness(120%) saturate(150%);
      }
      75% {
        filter: hue-rotate(270deg) brightness(110%) saturate(130%);
      }
      100% {
        filter: hue-rotate(360deg) brightness(100%) saturate(100%);
      }
    }

    .glitch-effect {
      animation: glitchFilters 0.3s ease-in-out infinite;
    }

    @keyframes glitchFilters {
      0% {
        filter: brightness(100%) contrast(100%);
      }
      10% {
        filter: brightness(150%) contrast(200%) hue-rotate(90deg);
      }
      20% {
        filter: brightness(50%) contrast(150%) hue-rotate(-90deg);
      }
      30% {
        filter: brightness(200%) contrast(50%) invert(100%);
      }
      40% {
        filter: brightness(100%) contrast(100%);
      }
      100% {
        filter: brightness(100%) contrast(100%);
      }
    }
  }

  /* Scroll-based combinations */
  .scroll-combinations {
    .parallax-filter {
      transition: filter 0.3s ease;
      filter: brightness(80%) contrast(90%);
    }

    .parallax-filter.in-view {
      filter: brightness(110%) contrast(120%) saturate(130%);
    }

    .scroll-reveal {
      filter: blur(10px) brightness(50%);
      transition: filter 1s ease;
    }

    .scroll-reveal.revealed {
      filter: blur(0) brightness(100%) contrast(110%);
    }
  }
}
```

## 4. Advanced Filter Techniques

### Performance และ Optimization

```css
/* การเพิ่มประสิทธิภาพ filters */
.filter-performance {
  /* Hardware acceleration */
  .accelerated-filters {
    .gpu-filter {
      filter: brightness(110%) contrast(120%);
      transform: translateZ(0);
      will-change: filter;
      /* บังคับใช้ GPU */
    }

    .contain-filter {
      filter: blur(5px) brightness(120%);
      contain: layout style paint;
      /* จำกัด scope ของ repaints */
    }
  }

  /* Efficient transitions */
  .efficient-transitions {
    .smooth-filter {
      filter: brightness(100%);
      transition: filter 0.3s ease;
      /* ใช้ transition แทน animation เมื่อเป็นไปได้ */
    }

    .smooth-filter:hover {
      filter: brightness(110%) contrast(110%);
    }

    /* Avoid expensive filter changes */
    .expensive-avoid {
      /* ❌ หลีกเลี่ยง: การเปลี่ยน blur มากๆ */
      transition: filter 0.5s ease;
    }

    .expensive-avoid:hover {
      filter: blur(20px); /* แพง! */
    }

    /* ✅ ดีกว่า: ใช้ pre-blurred version */
    .efficient-alternative {
      background-image: url('image.jpg');
      transition: opacity 0.3s ease;
    }

    .efficient-alternative::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-image: url('image-blurred.jpg');
      opacity: 0;
      transition: opacity 0.3s ease;
    }

    .efficient-alternative:hover::before {
      opacity: 1;
    }
  }

  /* Responsive filters */
  .responsive-filters {
    /* Mobile: reduced effects */
    .mobile-optimized {
      filter: brightness(105%);
    }

    @media (min-width: 768px) {
      .mobile-optimized {
        filter: brightness(110%) contrast(110%);
      }
    }

    @media (min-width: 1024px) {
      .mobile-optimized {
        filter: brightness(110%) contrast(110%) saturate(120%) blur(0.5px);
      }
    }

    /* Reduce motion */
    @media (prefers-reduced-motion: reduce) {
      .motion-sensitive {
        filter: brightness(105%) contrast(105%);
        animation: none;
        transition: none;
      }
    }

    /* High contrast */
    @media (prefers-contrast: high) {
      .contrast-adaptive {
        filter: brightness(120%) contrast(150%);
      }
    }
  }

  /* Battery optimization */
  .battery-optimization {
    .battery-aware {
      filter: brightness(100%);
    }

    /* CSS มี API สำหรับ battery แต่ limited support */
    .battery-save-mode {
      filter: brightness(90%);
      /* ลดความสว่างเล็กน้อยเพื่อประหยัดแบตเตอรี่ */
    }
  }
}
```

### Cross-browser Compatibility

```css
/* การรองรับ browsers ต่างๆ */
.filter-compatibility {
  /* Modern browsers */
  .modern-filter {
    filter: brightness(110%) contrast(120%) blur(2px);
    /* รองรับ browsers สมัยใหม่ */
  }

  /* Fallbacks for older browsers */
  .filter-fallback {
    /* Fallback for no filter support */
    opacity: 0.9;

    /* Modern filter */
    filter: brightness(90%);
  }

  /* Progressive enhancement */
  .progressive-filter {
    /* Base styles */
    background-color: #f0f0f0;

    /* Enhanced with filters */
    background-image: linear-gradient(45deg, #3b82f6, #8b5cf6);
  }

  @supports (filter: blur(1px)) {
    .progressive-filter {
      filter: brightness(110%) contrast(110%);
      /* เพิ่ม filter เมื่อ browser รองรับ */
    }
  }

  /* Vendor prefixes (mostly not needed anymore) */
  .vendor-prefixes {
    -webkit-filter: brightness(110%);
    -moz-filter: brightness(110%);
    -o-filter: brightness(110%);
    filter: brightness(110%);
    /* รองรับ browsers เก่า */
  }

  /* Feature detection */
  .feature-detection {
    /* CSS feature queries */
    background: #3b82f6;
  }

  @supports (filter: brightness(110%)) {
    .feature-detection {
      background: transparent;
      filter: brightness(110%);
    }
  }

  @supports not (filter: brightness(110%)) {
    .feature-detection {
      /* Alternative styling for unsupported browsers */
      background: #60a5fa;
      opacity: 0.9;
    }
  }
}
```

### Accessibility Considerations

```css
/* การพิจารณา accessibility */
.filter-accessibility {
  /* Respect user preferences */
  .accessible-filters {
    filter: brightness(105%) contrast(105%);
  }

  @media (prefers-contrast: high) {
    .accessible-filters {
      filter: brightness(110%) contrast(150%);
      /* เพิ่ม contrast สำหรับผู้ใช้ที่ต้องการ */
    }
  }

  @media (prefers-contrast: low) {
    .accessible-filters {
      filter: brightness(100%) contrast(90%);
      /* ลด contrast สำหรับผู้ใช้ที่ต้องการ */
    }
  }

  @media (prefers-reduced-motion: reduce) {
    .accessible-filters {
      /* ไม่ใช้ filter animations */
      animation: none;
      transition: none;
    }
  }

  /* Color blindness considerations */
  .colorblind-friendly {
    .protanopia-friendly {
      filter: hue-rotate(10deg) saturate(120%);
      /* ปรับสำหรับ red-green colorblind */
    }

    .deuteranopia-friendly {
      filter: hue-rotate(-10deg) saturate(110%);
      /* ปรับสำหรับ green-red colorblind */
    }

    .tritanopia-friendly {
      filter: hue-rotate(180deg) saturate(130%);
      /* ปรับสำหรับ blue-yellow colorblind */
    }
  }

  /* Focus visibility */
  .focus-visibility {
    .accessible-focus {
      filter: brightness(100%);
      transition: filter 0.2s ease;
    }

    .accessible-focus:focus {
      filter: brightness(120%) contrast(120%);
      outline: 2px solid #3b82f6;
      outline-offset: 2px;
      /* เพิ่มความชัดเจนของ focus */
    }

    .accessible-focus:focus-visible {
      filter: brightness(130%) contrast(130%);
      /* เพิ่มเติมสำหรับ keyboard navigation */
    }
  }

  /* Alternative content */
  .alternative-content {
    .filter-alternative {
      filter: blur(5px);
      position: relative;
    }

    .filter-alternative::after {
      content: attr(aria-label);
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: rgba(0, 0, 0, 0.8);
      color: white;
      padding: 8px 12px;
      border-radius: 4px;
      font-size: 14px;
      white-space: nowrap;
      /* แสดงข้อความทดแทนเมื่อเบลอ */
    }
  }
}
```

## สรุป: CSS Filters Best Practices

### Key Concepts 🎯

1. **blur(): การเบลอ**

   ```css
   .blur {
     filter: blur(5px);
   }
   ```

2. **brightness(): ความสว่าง**

   ```css
   .bright {
     filter: brightness(120%);
   }
   ```

3. **การรวม filters**

   ```css
   .combined {
     filter: blur(2px) brightness(110%) contrast(120%);
   }
   ```

4. **Performance considerations**
   - ใช้ `will-change: filter` สำหรับ animations
   - ระวัง `blur()` values สูงกับ performance
   - ให้ fallbacks สำหรับ browsers เก่า

### Quick Reference 📋

```css
/* Common filter combinations */
.filter-presets {
  /* Instagram-style */
  .vintage {
    filter: sepia(50%) contrast(120%) brightness(110%);
  }
  .dramatic {
    filter: contrast(150%) brightness(80%) saturate(200%);
  }
  .soft {
    filter: blur(1px) brightness(105%) contrast(95%);
  }

  /* Interactive states */
  .hover-brighten:hover {
    filter: brightness(110%);
  }
  .focus-sharp:focus {
    filter: blur(0) brightness(110%) contrast(110%);
  }

  /* Accessibility-friendly */
  .high-contrast {
    filter: brightness(110%) contrast(150%);
  }
  .reduced-motion {
    filter: brightness(105%);
    animation: none;
  }
}
```

### Performance Tips 🚀

```css
/* Efficient filter usage */
.efficient-filters {
  /* ✅ Good: Simple filters */
  .good {
    filter: brightness(110%) contrast(110%);
  }

  /* ❌ Expensive: Heavy blur */
  .expensive {
    filter: blur(20px);
  }

  /* ✅ Better: Pre-processed images */
  .optimized {
    background: url('optimized-image.jpg');
    filter: brightness(105%);
  }

  /* ✅ GPU acceleration */
  .accelerated {
    filter: brightness(110%);
    transform: translateZ(0);
    will-change: filter;
  }
}
```

CSS Filters เป็นเครื่องมือที่ทรงพลังในการสร้างเอฟเฟกต์ภาพที่หลากหลาย ช่วยเพิ่มความสวยงามและการโต้ตอบให้กับเว็บไซต์!
