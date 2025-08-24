# Flexbox Common Patterns: Navbar & Equal-Height Cards

## ภาพรวม Common Patterns

Flexbox Patterns เป็นรูปแบบการใช้งาน Flexbox ที่ได้รับความนิยมและใช้บ่อยในการพัฒนาเว็บไซต์ โดยเฉพาะ **Navigation Bar** และ **Equal-Height Cards** ที่เป็นองค์ประกอบพื้นฐานของเว็บไซต์สมัยใหม่

### แนวคิดหลักของ Patterns

```css
/* Core Flexbox Pattern Concepts */
.pattern-fundamentals {
  /* 1. Container Properties */
  display: flex;
  justify-content: space-between; /* กระจาย space */
  align-items: center; /* จัดกึ่งกลาง cross axis */

  /* 2. Item Properties */
  flex: 1; /* ขยายเต็มพื้นที่ */
  flex-shrink: 0; /* ป้องกันการหด */

  /* 3. Responsive Behavior */
  flex-direction: column; /* Mobile first */
  flex-wrap: wrap; /* อนุญาตการ wrap */
}
```

## 1. Navigation Bar Patterns 🧭

### Basic Navbar Structure

```css
/* พื้นฐาน Navbar ด้วย Flexbox */
.navbar-basic {
  /* Container Setup */
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    border-bottom: 1px solid #e5e7eb;
  }

  /* Logo Section */
  .navbar-brand {
    flex-shrink: 0; /* ไม่ให้ logo หด */
    font-size: 1.5rem;
    font-weight: bold;
    color: #1f2937;
    text-decoration: none;
  }

  /* Navigation Menu */
  .navbar-nav {
    display: flex;
    align-items: center;
    gap: 2rem;
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .nav-link {
    color: #6b7280;
    text-decoration: none;
    font-weight: 500;
    padding: 0.5rem 0;
    transition: color 0.2s ease;
    position: relative;
  }

  .nav-link:hover {
    color: #3b82f6;
  }

  .nav-link.active {
    color: #3b82f6;
  }

  .nav-link.active::after {
    content: '';
    position: absolute;
    bottom: -1rem;
    left: 0;
    right: 0;
    height: 2px;
    background: #3b82f6;
  }

  /* User Actions */
  .navbar-actions {
    display: flex;
    align-items: center;
    gap: 1rem;
    flex-shrink: 0; /* ไม่ให้ actions หด */
  }

  .btn-login {
    padding: 0.5rem 1rem;
    background: transparent;
    color: #6b7280;
    border: 1px solid #d1d5db;
    border-radius: 0.375rem;
    text-decoration: none;
    transition: all 0.2s ease;
  }

  .btn-login:hover {
    background: #f3f4f6;
    border-color: #9ca3af;
  }

  .btn-signup {
    padding: 0.5rem 1rem;
    background: #3b82f6;
    color: white;
    border: none;
    border-radius: 0.375rem;
    text-decoration: none;
    transition: background 0.2s ease;
  }

  .btn-signup:hover {
    background: #2563eb;
  }
}
```

### Responsive Navbar

```css
/* Responsive Navigation Bar */
.navbar-responsive {
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    position: relative;
  }

  /* Mobile Menu Toggle */
  .navbar-toggle {
    display: none;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 2rem;
    height: 2rem;
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 0;
  }

  .navbar-toggle span {
    display: block;
    width: 1.5rem;
    height: 2px;
    background: #374151;
    margin: 2px 0;
    transition: all 0.3s ease;
  }

  /* Desktop Navigation */
  .navbar-nav {
    display: flex;
    align-items: center;
    gap: 2rem;
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .navbar-actions {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  /* Mobile Styles */
  @media (max-width: 768px) {
    .navbar-toggle {
      display: flex;
    }

    .navbar-nav {
      position: absolute;
      top: 100%;
      left: 0;
      right: 0;
      background: white;
      flex-direction: column;
      align-items: stretch;
      gap: 0;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      border-top: 1px solid #e5e7eb;
      padding: 1rem 0;
      transform: translateY(-100%);
      opacity: 0;
      visibility: hidden;
      transition: all 0.3s ease;
    }

    .navbar-nav.active {
      transform: translateY(0);
      opacity: 1;
      visibility: visible;
    }

    .nav-item {
      border-bottom: 1px solid #f3f4f6;
    }

    .nav-item:last-child {
      border-bottom: none;
    }

    .nav-link {
      display: block;
      padding: 1rem 2rem;
      color: #374151;
      border-bottom: none;
    }

    .nav-link.active::after {
      display: none;
    }

    .navbar-actions {
      position: absolute;
      top: 100%;
      left: 0;
      right: 0;
      background: #f8fafc;
      flex-direction: column;
      align-items: stretch;
      gap: 1rem;
      padding: 1rem 2rem;
      border-top: 1px solid #e5e7eb;
      transform: translateY(-100%);
      opacity: 0;
      visibility: hidden;
      transition: all 0.3s ease;
    }

    .navbar-actions.active {
      transform: translateY(0);
      opacity: 1;
      visibility: visible;
    }

    .btn-login,
    .btn-signup {
      text-align: center;
    }
  }

  /* Tablet Styles */
  @media (min-width: 769px) and (max-width: 1024px) {
    .navbar-nav {
      gap: 1.5rem;
    }

    .navbar {
      padding: 1rem 1.5rem;
    }
  }
}
```

### Advanced Navbar Patterns

```css
/* Advanced Navbar Variations */
.navbar-advanced {
  /* Navbar with Search */
  .navbar-with-search {
    display: flex;
    align-items: center;
    gap: 2rem;
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .navbar-brand {
    flex-shrink: 0;
  }

  .navbar-search {
    flex: 1;
    max-width: 400px;
    position: relative;
  }

  .search-input {
    width: 100%;
    padding: 0.75rem 1rem 0.75rem 2.5rem;
    border: 1px solid #d1d5db;
    border-radius: 0.5rem;
    font-size: 0.875rem;
    background: #f8fafc;
    transition: all 0.2s ease;
  }

  .search-input:focus {
    outline: none;
    border-color: #3b82f6;
    box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
    background: white;
  }

  .search-icon {
    position: absolute;
    left: 0.75rem;
    top: 50%;
    transform: translateY(-50%);
    color: #9ca3af;
    width: 1rem;
    height: 1rem;
  }

  .navbar-nav {
    display: flex;
    align-items: center;
    gap: 1.5rem;
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .navbar-actions {
    display: flex;
    align-items: center;
    gap: 1rem;
    flex-shrink: 0;
  }

  /* Navbar with Dropdown */
  .navbar-with-dropdown {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .nav-dropdown {
    position: relative;
  }

  .dropdown-toggle {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.5rem 0;
    background: transparent;
    border: none;
    color: #6b7280;
    cursor: pointer;
    font-weight: 500;
  }

  .dropdown-toggle:hover {
    color: #3b82f6;
  }

  .dropdown-icon {
    width: 1rem;
    height: 1rem;
    transition: transform 0.2s ease;
  }

  .nav-dropdown.active .dropdown-icon {
    transform: rotate(180deg);
  }

  .dropdown-menu {
    position: absolute;
    top: 100%;
    left: 0;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
    border: 1px solid #e5e7eb;
    min-width: 200px;
    padding: 0.5rem 0;
    opacity: 0;
    visibility: hidden;
    transform: translateY(-10px);
    transition: all 0.2s ease;
    z-index: 50;
  }

  .nav-dropdown.active .dropdown-menu {
    opacity: 1;
    visibility: visible;
    transform: translateY(0);
  }

  .dropdown-item {
    display: block;
    padding: 0.75rem 1rem;
    color: #374151;
    text-decoration: none;
    transition: background 0.2s ease;
  }

  .dropdown-item:hover {
    background: #f3f4f6;
    color: #1f2937;
  }

  .dropdown-divider {
    height: 1px;
    background: #e5e7eb;
    margin: 0.5rem 0;
  }

  /* Navbar with User Profile */
  .user-profile {
    position: relative;
  }

  .profile-toggle {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.5rem;
    background: transparent;
    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
    transition: background 0.2s ease;
  }

  .profile-toggle:hover {
    background: #f3f4f6;
  }

  .profile-avatar {
    width: 2rem;
    height: 2rem;
    border-radius: 50%;
    object-fit: cover;
  }

  .profile-info {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    text-align: left;
  }

  .profile-name {
    font-size: 0.875rem;
    font-weight: 500;
    color: #1f2937;
    line-height: 1.2;
  }

  .profile-role {
    font-size: 0.75rem;
    color: #6b7280;
    line-height: 1.2;
  }

  .profile-dropdown {
    position: absolute;
    top: 100%;
    right: 0;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
    border: 1px solid #e5e7eb;
    min-width: 220px;
    padding: 0.5rem 0;
    opacity: 0;
    visibility: hidden;
    transform: translateY(-10px);
    transition: all 0.2s ease;
    z-index: 50;
  }

  .user-profile.active .profile-dropdown {
    opacity: 1;
    visibility: visible;
    transform: translateY(0);
  }
}
```

### Navbar with Mega Menu

```css
/* Mega Menu Navbar */
.navbar-mega {
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    position: relative;
  }

  .mega-menu-trigger {
    position: relative;
  }

  .mega-menu-toggle {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.75rem 1rem;
    background: transparent;
    border: none;
    color: #6b7280;
    cursor: pointer;
    font-weight: 500;
    border-radius: 0.375rem;
    transition: all 0.2s ease;
  }

  .mega-menu-toggle:hover {
    background: #f3f4f6;
    color: #1f2937;
  }

  .mega-menu {
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    background: white;
    border-radius: 0.75rem;
    box-shadow: 0 20px 25px rgba(0, 0, 0, 0.1);
    border: 1px solid #e5e7eb;
    width: 800px;
    max-width: 90vw;
    padding: 2rem;
    opacity: 0;
    visibility: hidden;
    transform: translateX(-50%) translateY(-20px);
    transition: all 0.3s ease;
    z-index: 50;
  }

  .mega-menu-trigger.active .mega-menu {
    opacity: 1;
    visibility: visible;
    transform: translateX(-50%) translateY(0);
  }

  .mega-menu-content {
    display: flex;
    gap: 3rem;
  }

  .mega-menu-section {
    flex: 1;
  }

  .mega-menu-title {
    font-size: 1rem;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 1rem;
    padding-bottom: 0.5rem;
    border-bottom: 2px solid #e5e7eb;
  }

  .mega-menu-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .mega-menu-item {
    margin-bottom: 0.75rem;
  }

  .mega-menu-link {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.5rem 0;
    color: #6b7280;
    text-decoration: none;
    transition: color 0.2s ease;
  }

  .mega-menu-link:hover {
    color: #3b82f6;
  }

  .mega-menu-icon {
    width: 1.25rem;
    height: 1.25rem;
    color: #9ca3af;
  }

  .mega-menu-text {
    flex: 1;
  }

  .mega-menu-label {
    display: block;
    font-weight: 500;
    margin-bottom: 0.125rem;
  }

  .mega-menu-description {
    font-size: 0.875rem;
    color: #9ca3af;
  }

  /* Featured Section */
  .mega-menu-featured {
    flex: 0 0 300px;
    background: #f8fafc;
    border-radius: 0.5rem;
    padding: 1.5rem;
  }

  .featured-title {
    font-size: 1.125rem;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 0.5rem;
  }

  .featured-description {
    color: #6b7280;
    margin-bottom: 1rem;
    line-height: 1.5;
  }

  .featured-cta {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.75rem 1.5rem;
    background: #3b82f6;
    color: white;
    text-decoration: none;
    border-radius: 0.375rem;
    font-weight: 500;
    transition: background 0.2s ease;
  }

  .featured-cta:hover {
    background: #2563eb;
  }
}
```

## 2. Equal-Height Cards Patterns 🃏

### Basic Equal-Height Cards

```css
/* พื้นฐาน Equal-Height Cards */
.cards-equal-height {
  /* Container Setup */
  .card-container {
    display: flex;
    gap: 1.5rem;
    padding: 2rem;
    align-items: stretch; /* สำคัญ! ทำให้ cards สูงเท่ากัน */
  }

  /* Card Structure */
  .card {
    flex: 1; /* แบ่ง space เท่าๆ กัน */
    display: flex;
    flex-direction: column; /* สำคัญ! เพื่อจัด layout ภายใน */
    background: white;
    border-radius: 0.75rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    transition: all 0.3s ease;
  }

  .card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
  }

  /* Card Image */
  .card-image {
    width: 100%;
    height: 200px;
    object-fit: cover;
    flex-shrink: 0; /* ไม่ให้รูปหด */
  }

  /* Card Content */
  .card-content {
    flex: 1; /* ขยายเต็มพื้นที่ที่เหลือ */
    display: flex;
    flex-direction: column;
    padding: 1.5rem;
  }

  .card-category {
    display: inline-flex;
    align-items: center;
    width: fit-content;
    padding: 0.25rem 0.75rem;
    background: #eff6ff;
    color: #3b82f6;
    border-radius: 9999px;
    font-size: 0.75rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    margin-bottom: 1rem;
  }

  .card-title {
    font-size: 1.25rem;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 0.75rem;
    line-height: 1.4;
  }

  .card-description {
    flex: 1; /* ขยายเต็มพื้นที่ */
    color: #6b7280;
    line-height: 1.6;
    margin-bottom: 1.5rem;
  }

  /* Card Footer */
  .card-footer {
    margin-top: auto; /* ผลักไปด้านล่างเสมอ */
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 1rem;
    border-top: 1px solid #f3f4f6;
  }

  .card-author {
    display: flex;
    align-items: center;
    gap: 0.75rem;
  }

  .author-avatar {
    width: 2rem;
    height: 2rem;
    border-radius: 50%;
    object-fit: cover;
  }

  .author-info {
    display: flex;
    flex-direction: column;
  }

  .author-name {
    font-size: 0.875rem;
    font-weight: 500;
    color: #1f2937;
    line-height: 1.2;
  }

  .author-date {
    font-size: 0.75rem;
    color: #9ca3af;
    line-height: 1.2;
  }

  .card-actions {
    display: flex;
    gap: 0.5rem;
  }

  .card-action {
    padding: 0.5rem;
    background: #f8fafc;
    border: 1px solid #e5e7eb;
    border-radius: 0.375rem;
    color: #6b7280;
    text-decoration: none;
    transition: all 0.2s ease;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .card-action:hover {
    background: #3b82f6;
    color: white;
    border-color: #3b82f6;
  }

  .action-icon {
    width: 1rem;
    height: 1rem;
  }
}
```

### Responsive Equal-Height Cards

```css
/* Responsive Card Grid */
.cards-responsive {
  .card-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 1.5rem;
    padding: 2rem;
    align-items: stretch;
  }

  .card {
    flex: 1 1 100%; /* Mobile: 1 column */
    min-width: 0; /* ป้องกัน overflow */
    display: flex;
    flex-direction: column;
    background: white;
    border-radius: 0.75rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
  }

  /* Tablet: 2 columns */
  @media (min-width: 640px) {
    .card {
      flex: 1 1 calc(50% - 0.75rem);
    }
  }

  /* Desktop: 3 columns */
  @media (min-width: 1024px) {
    .card {
      flex: 1 1 calc(33.333% - 1rem);
    }
  }

  /* Large Desktop: 4 columns */
  @media (min-width: 1280px) {
    .card {
      flex: 1 1 calc(25% - 1.125rem);
    }
  }

  /* Ensure minimum card width */
  .card {
    min-width: 280px; /* ขนาดขั้นต่ำ */
  }

  /* Card content responsive adjustments */
  @media (max-width: 639px) {
    .card-content {
      padding: 1rem;
    }

    .card-title {
      font-size: 1.125rem;
    }

    .card-footer {
      flex-direction: column;
      align-items: stretch;
      gap: 1rem;
    }

    .card-actions {
      justify-content: center;
    }
  }
}
```

### Advanced Card Variations

```css
/* Advanced Card Patterns */
.cards-advanced {
  /* Pricing Cards */
  .pricing-cards {
    display: flex;
    gap: 1.5rem;
    padding: 2rem;
    align-items: stretch;
  }

  .pricing-card {
    flex: 1;
    display: flex;
    flex-direction: column;
    background: white;
    border-radius: 1rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    position: relative;
  }

  .pricing-card.featured {
    transform: scale(1.05);
    border: 2px solid #3b82f6;
    box-shadow: 0 8px 25px rgba(59, 130, 246, 0.2);
  }

  .pricing-card.featured::before {
    content: 'Most Popular';
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    background: #3b82f6;
    color: white;
    padding: 0.5rem 2rem;
    border-radius: 0 0 1rem 1rem;
    font-size: 0.875rem;
    font-weight: 600;
  }

  .pricing-header {
    padding: 2rem 1.5rem 1rem;
    text-align: center;
    background: linear-gradient(135deg, #f8fafc 0%, #e5e7eb 100%);
  }

  .pricing-card.featured .pricing-header {
    background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
    color: white;
  }

  .pricing-title {
    font-size: 1.5rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
  }

  .pricing-price {
    font-size: 3rem;
    font-weight: bold;
    margin-bottom: 0.25rem;
  }

  .pricing-period {
    color: #6b7280;
    font-size: 0.875rem;
  }

  .pricing-card.featured .pricing-period {
    color: rgba(255, 255, 255, 0.8);
  }

  .pricing-body {
    flex: 1;
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
  }

  .pricing-features {
    flex: 1;
    list-style: none;
    padding: 0;
    margin: 0 0 1.5rem 0;
  }

  .pricing-feature {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.75rem 0;
    border-bottom: 1px solid #f3f4f6;
  }

  .pricing-feature:last-child {
    border-bottom: none;
  }

  .feature-icon {
    width: 1.25rem;
    height: 1.25rem;
    color: #22c55e;
    flex-shrink: 0;
  }

  .feature-text {
    color: #374151;
    line-height: 1.5;
  }

  .pricing-cta {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 0.75rem 1.5rem;
    background: #f3f4f6;
    color: #374151;
    border: 2px solid #e5e7eb;
    border-radius: 0.5rem;
    text-decoration: none;
    font-weight: 600;
    transition: all 0.2s ease;
    margin-top: auto;
  }

  .pricing-cta:hover {
    background: #374151;
    color: white;
    border-color: #374151;
  }

  .pricing-card.featured .pricing-cta {
    background: #3b82f6;
    color: white;
    border-color: #3b82f6;
  }

  .pricing-card.featured .pricing-cta:hover {
    background: #2563eb;
    border-color: #2563eb;
  }

  /* Feature Cards */
  .feature-cards {
    display: flex;
    gap: 1.5rem;
    padding: 2rem;
    align-items: stretch;
  }

  .feature-card {
    flex: 1;
    display: flex;
    flex-direction: column;
    background: white;
    border-radius: 0.75rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 2rem;
    text-align: center;
    transition: all 0.3s ease;
  }

  .feature-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
  }

  .feature-icon-wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 4rem;
    height: 4rem;
    background: linear-gradient(135deg, #3b82f6, #8b5cf6);
    border-radius: 1rem;
    margin: 0 auto 1.5rem;
  }

  .feature-icon {
    width: 2rem;
    height: 2rem;
    color: white;
  }

  .feature-title {
    font-size: 1.25rem;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 1rem;
  }

  .feature-description {
    flex: 1;
    color: #6b7280;
    line-height: 1.6;
    margin-bottom: 1.5rem;
  }

  .feature-link {
    color: #3b82f6;
    text-decoration: none;
    font-weight: 500;
    transition: color 0.2s ease;
    margin-top: auto;
  }

  .feature-link:hover {
    color: #2563eb;
  }

  /* Team Cards */
  .team-cards {
    display: flex;
    gap: 1.5rem;
    padding: 2rem;
    align-items: stretch;
  }

  .team-card {
    flex: 1;
    display: flex;
    flex-direction: column;
    background: white;
    border-radius: 0.75rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    text-align: center;
  }

  .team-avatar {
    width: 100%;
    height: 250px;
    object-fit: cover;
  }

  .team-info {
    flex: 1;
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
  }

  .team-name {
    font-size: 1.25rem;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 0.5rem;
  }

  .team-role {
    color: #3b82f6;
    font-weight: 500;
    margin-bottom: 1rem;
  }

  .team-bio {
    flex: 1;
    color: #6b7280;
    line-height: 1.6;
    margin-bottom: 1.5rem;
  }

  .team-social {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin-top: auto;
  }

  .social-link {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 2.5rem;
    height: 2.5rem;
    background: #f3f4f6;
    color: #6b7280;
    border-radius: 50%;
    text-decoration: none;
    transition: all 0.2s ease;
  }

  .social-link:hover {
    background: #3b82f6;
    color: white;
  }

  .social-icon {
    width: 1rem;
    height: 1rem;
  }
}
```

### Card Masonry Layout

```css
/* Masonry-style Cards (CSS Grid alternative) */
.cards-masonry {
  .masonry-container {
    display: flex;
    flex-wrap: wrap;
    gap: 1.5rem;
    padding: 2rem;
    align-items: flex-start; /* สำคัญ! ไม่ใช้ stretch */
  }

  .masonry-card {
    flex: 1 1 calc(33.333% - 1rem);
    min-width: 300px;
    background: white;
    border-radius: 0.75rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    break-inside: avoid; /* สำหรับ browser ที่รองรับ */
  }

  /* Responsive breakpoints */
  @media (max-width: 1023px) {
    .masonry-card {
      flex: 1 1 calc(50% - 0.75rem);
    }
  }

  @media (max-width: 639px) {
    .masonry-card {
      flex: 1 1 100%;
    }
  }

  /* Variable height content */
  .masonry-image {
    width: 100%;
    height: auto; /* ความสูงตามอัตราส่วน */
    display: block;
  }

  .masonry-content {
    padding: 1.5rem;
  }

  .masonry-title {
    font-size: 1.125rem;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 0.75rem;
  }

  .masonry-text {
    color: #6b7280;
    line-height: 1.6;
    margin-bottom: 1rem;
  }

  .masonry-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .masonry-tag {
    padding: 0.25rem 0.75rem;
    background: #f3f4f6;
    color: #6b7280;
    border-radius: 9999px;
    font-size: 0.75rem;
    font-weight: 500;
  }
}
```

## 3. Combining Patterns: Navbar + Cards Layout

### Complete Page Layout

```css
/* รวม Navbar และ Cards ในหน้าเดียว */
.complete-layout {
  /* Page Structure */
  .page-wrapper {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  /* Navbar (ใช้ pattern ที่ได้เรียนรู้) */
  .main-navbar {
    flex-shrink: 0; /* ไม่ให้ navbar หด */
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    border-bottom: 1px solid #e5e7eb;
    position: sticky;
    top: 0;
    z-index: 100;
  }

  /* Main Content Area */
  .main-content {
    flex: 1; /* ขยายเต็มพื้นที่ที่เหลือ */
    background: #f8fafc;
  }

  /* Hero Section */
  .hero-section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 4rem 2rem;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
  }

  .hero-title {
    font-size: 3rem;
    font-weight: bold;
    margin-bottom: 1rem;
  }

  .hero-subtitle {
    font-size: 1.25rem;
    margin-bottom: 2rem;
    opacity: 0.9;
  }

  .hero-cta {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 1rem 2rem;
    background: white;
    color: #667eea;
    border-radius: 0.5rem;
    text-decoration: none;
    font-weight: 600;
    transition: all 0.3s ease;
  }

  .hero-cta:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
  }

  /* Cards Section */
  .cards-section {
    padding: 4rem 2rem;
  }

  .section-header {
    text-align: center;
    margin-bottom: 3rem;
  }

  .section-title {
    font-size: 2.5rem;
    font-weight: bold;
    color: #1f2937;
    margin-bottom: 1rem;
  }

  .section-description {
    font-size: 1.125rem;
    color: #6b7280;
    max-width: 600px;
    margin: 0 auto;
    line-height: 1.6;
  }

  /* Cards Grid (ใช้ equal-height pattern) */
  .cards-wrapper {
    max-width: 1200px;
    margin: 0 auto;
  }

  .cards-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 2rem;
    align-items: stretch;
  }

  .content-card {
    flex: 1 1 calc(33.333% - 1.333rem);
    min-width: 300px;
    display: flex;
    flex-direction: column;
    background: white;
    border-radius: 0.75rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    transition: all 0.3s ease;
  }

  .content-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
  }

  /* Responsive adjustments */
  @media (max-width: 1023px) {
    .content-card {
      flex: 1 1 calc(50% - 1rem);
    }

    .hero-title {
      font-size: 2.5rem;
    }

    .section-title {
      font-size: 2rem;
    }
  }

  @media (max-width: 639px) {
    .content-card {
      flex: 1 1 100%;
    }

    .hero-title {
      font-size: 2rem;
    }

    .hero-section {
      padding: 2rem 1rem;
    }

    .cards-section {
      padding: 2rem 1rem;
    }

    .cards-grid {
      gap: 1rem;
    }
  }

  /* Footer */
  .main-footer {
    flex-shrink: 0;
    background: #1f2937;
    color: white;
    padding: 2rem;
    text-align: center;
  }
}
```

## 4. Interactive Enhancements

### JavaScript for Pattern Interactions

```javascript
// JavaScript สำหรับ Navbar และ Cards
class FlexboxPatterns {
  constructor() {
    this.initNavbar();
    this.initCards();
  }

  // Navbar interactions
  initNavbar() {
    // Mobile menu toggle
    const navbarToggle = document.querySelector('.navbar-toggle');
    const navbarNav = document.querySelector('.navbar-nav');
    const navbarActions = document.querySelector('.navbar-actions');

    if (navbarToggle) {
      navbarToggle.addEventListener('click', () => {
        navbarNav?.classList.toggle('active');
        navbarActions?.classList.toggle('active');

        // Animate hamburger icon
        const spans = navbarToggle.querySelectorAll('span');
        spans.forEach((span, index) => {
          if (navbarNav?.classList.contains('active')) {
            if (index === 0)
              span.style.transform = 'rotate(45deg) translate(5px, 5px)';
            if (index === 1) span.style.opacity = '0';
            if (index === 2)
              span.style.transform = 'rotate(-45deg) translate(7px, -6px)';
          } else {
            span.style.transform = 'none';
            span.style.opacity = '1';
          }
        });
      });
    }

    // Dropdown menus
    const dropdownTriggers = document.querySelectorAll(
      '.dropdown-toggle, .mega-menu-toggle'
    );
    dropdownTriggers.forEach((trigger) => {
      trigger.addEventListener('click', (e) => {
        e.preventDefault();
        const parent = trigger.closest('.nav-dropdown, .mega-menu-trigger');
        const isActive = parent?.classList.contains('active');

        // Close all other dropdowns
        document
          .querySelectorAll('.nav-dropdown.active, .mega-menu-trigger.active')
          .forEach((item) => item.classList.remove('active'));

        // Toggle current dropdown
        if (!isActive) {
          parent?.classList.add('active');
        }
      });
    });

    // Close dropdowns when clicking outside
    document.addEventListener('click', (e) => {
      if (!e.target.closest('.nav-dropdown, .mega-menu-trigger')) {
        document
          .querySelectorAll('.nav-dropdown.active, .mega-menu-trigger.active')
          .forEach((item) => item.classList.remove('active'));
      }
    });

    // User profile dropdown
    const profileToggle = document.querySelector('.profile-toggle');
    const userProfile = document.querySelector('.user-profile');

    if (profileToggle) {
      profileToggle.addEventListener('click', (e) => {
        e.preventDefault();
        userProfile?.classList.toggle('active');
      });
    }
  }

  // Card interactions
  initCards() {
    // Card hover effects
    const cards = document.querySelectorAll(
      '.card, .pricing-card, .feature-card'
    );
    cards.forEach((card) => {
      card.addEventListener('mouseenter', () => {
        card.style.transform = 'translateY(-4px)';
        card.style.boxShadow = '0 8px 25px rgba(0, 0, 0, 0.15)';
      });

      card.addEventListener('mouseleave', () => {
        if (!card.classList.contains('featured')) {
          card.style.transform = 'translateY(0)';
          card.style.boxShadow = '0 4px 6px rgba(0, 0, 0, 0.1)';
        }
      });
    });

    // Card action buttons
    const cardActions = document.querySelectorAll('.card-action');
    cardActions.forEach((action) => {
      action.addEventListener('click', (e) => {
        e.preventDefault();
        // Add your action logic here
        console.log('Card action clicked:', action.getAttribute('data-action'));
      });
    });

    // Pricing card selection
    const pricingCards = document.querySelectorAll('.pricing-card');
    pricingCards.forEach((card) => {
      const cta = card.querySelector('.pricing-cta');
      if (cta) {
        cta.addEventListener('click', (e) => {
          e.preventDefault();
          // Add selection logic
          pricingCards.forEach((c) => c.classList.remove('selected'));
          card.classList.add('selected');
          console.log(
            'Pricing plan selected:',
            card.querySelector('.pricing-title')?.textContent
          );
        });
      }
    });
  }

  // Utility method for responsive behavior
  handleResize() {
    const navbar = document.querySelector('.navbar');
    const navbarNav = document.querySelector('.navbar-nav');

    if (window.innerWidth > 768) {
      navbarNav?.classList.remove('active');
      // Reset mobile menu styles
      const hamburgerSpans = document.querySelectorAll('.navbar-toggle span');
      hamburgerSpans.forEach((span) => {
        span.style.transform = 'none';
        span.style.opacity = '1';
      });
    }
  }
}

// Initialize when DOM is loaded
document.addEventListener('DOMContentLoaded', () => {
  const patterns = new FlexboxPatterns();

  // Handle window resize
  window.addEventListener('resize', () => {
    patterns.handleResize();
  });
});
```

## สรุป: Best Practices สำหรับ Flexbox Patterns

### Key Principles 🎯

1. **Navbar Patterns**

   - ใช้ `justify-content: space-between` สำหรับ layout หลัก
   - ใช้ `align-items: center` สำหรับการจัดวางแนวตั้ง
   - ใช้ `flex-shrink: 0` สำหรับ logo และ actions
   - คิด mobile-first สำหรับ responsive design

2. **Equal-Height Cards**

   - ใช้ `align-items: stretch` ใน container
   - ใช้ `flex-direction: column` ใน card
   - ใช้ `flex: 1` สำหรับ content area
   - ใช้ `margin-top: auto` สำหรับ footer

3. **Responsive Design**

   - เริ่มจาก mobile layout
   - ใช้ `flex-wrap` สำหรับ grid behavior
   - ปรับ `flex-basis` ตาม breakpoint
   - ทดสอบใน device จริง

4. **Performance & Accessibility**
   - ใช้ semantic HTML
   - เพิ่ม focus states
   - ใช้ proper ARIA labels
   - ทดสอบ keyboard navigation

### Common Mistakes to Avoid ❌

```css
/* ❌ หลีกเลี่ยง */
.avoid-these {
  /* ไม่ใช้ height: 100% โดยไม่มี context */
  height: 100%; /* อาจไม่ทำงาน */

  /* ไม่ลืม flex-direction ใน card */
  /* display: flex; ไม่พอ ต้องมี flex-direction: column */

  /* ไม่ใช้ fixed width ใน responsive */
  width: 300px; /* แข็งเกินไป */
}

/* ✅ ใช้แทน */
.use-these {
  min-height: 100vh; /* ดีกว่า height: 100% */

  display: flex;
  flex-direction: column; /* ระบุชัดเจน */

  flex: 1 1 300px; /* ยืดหยุ่นกว่า */
  min-width: 280px; /* ขนาดขั้นต่ำ */
}
```

Flexbox Patterns เหล่านี้เป็นพื้นฐานสำคัญที่จะช่วยให้คุณสร้าง UI ที่สวยงาม ใช้งานง่าย และ responsive ได้อย่างมีประสิทธิภาพ! 🚀
