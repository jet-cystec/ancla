---
name: Cystec Branding & Design System
description: Complete branding scaffold for creating professional, premium web experiences with Cystec's design language - green palette, modern aesthetics, cloud-focused messaging
---

# Cystec Branding & Design System Skill

This skill encapsulates the complete design language, component library, and branding guidelines extracted from **cystec.global** (ancla project). Use this skill to create consistent, premium web experiences with the Cystec brand identity.

## 🎨 Design Philosophy

**Core Principles:**
- **Premium First Impressions**: Rich, vibrant aesthetics that WOW users immediately
- **Nature-Inspired Resilience**: Design inspired by nature's resilience and universe's grandeur
- **Clean & Modern**: Glassmorphism, smooth gradients, micro-animations
- **Cloud-Focused Messaging**: Technology with purpose, collaborative solutions

## 🌈 Color Palette

### Primary: Green Spectrum
The brand uses a rich green palette symbolizing growth, technology, and nature:

```javascript
// Tailwind Custom Green Configuration
colors: {
  green: {
    50: '#f0fdf4',   // Very light backgrounds, subtle accents
    100: '#dcfce7',  // Light backgrounds, hover states
    200: '#bbf7d0',  // Soft accents
    300: '#86efac',  // Medium accents
    400: '#4ade80',  // Bright highlights, CTAs (Hero button glow)
    500: '#22c55e',  // Primary CTA background
    600: '#16a34a',  // Primary hover states
    700: '#15803d',  // Text accents, icons
    800: '#166534',  // Dark buttons, bold text
    900: '#14532d',  // Primary dark (navbar, sections, headings)
    950: '#052e16',  // Deepest dark (hero overlay, footer)
  }
}
```

### Usage Patterns

| Element | Color | Usage |
|---------|-------|-------|
| **Hero Background Overlay** | `green-950/90` to `green-900/20` | Gradient overlay on hero image |
| **Primary Headings** | `green-900` | Main section titles |
| **CTA Buttons (Primary)** | `green-500` hover `green-400` | Main action buttons |
| **CTA Buttons (Dark)** | `green-900` hover `green-800` | Secondary actions |
| **Accent Text** | `green-400` or `green-600` | Highlighted keywords in headings |
| **Icon Containers** | `green-50` bg, `green-700` icon | Service card icons (light mode) |
| **Icon Hover** | `green-900` bg, `green-400` icon | Service card hover state |
| **Links Hover** | `green-600` or `green-700` | Navigation and footer links |

### Neutral Palette
```
gray-50  - Light section backgrounds
gray-100 - Borders, subtle dividers
gray-200 - Form field borders (inactive)
gray-400 - Muted text, placeholders
gray-500 - Body text (secondary)
gray-600 - Body text (primary)
gray-700 - Navbar text (scrolled)
gray-800 - Headings, strong text
gray-900 - Darkest text
white    - Primary background, inverse text
```

## 📐 Layout & Structure

### Container Pattern
```html
<div class="container mx-auto px-6">
  <!-- Centered content with responsive padding -->
</div>
```

### Section Spacing
```html
<!-- Standard section -->
<section class="py-24 bg-white">
  <!-- 96px (24 * 4px) vertical padding -->
</section>
```

### Responsive Grid
```html
<!-- Services grid: 1 col mobile, 2 tablet, 4 desktop -->
<div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
  <!-- Cards -->
</div>

<!-- Results grid: 1 col mobile, 2 desktop -->
<div class="grid md:grid-cols-2 gap-6 max-w-4xl mx-auto">
  <!-- Items -->
</div>
```

## 🧩 Component Library

### 1. Navigation Bar (Fixed, Scroll-Reactive)

**Features:**
- Transparent on top, white on scroll
- Logo filter changes (white → color)
- Text color changes (white → dark)
- Mobile hamburger menu
- Smooth transitions

**HTML Structure:**
```html
<nav id="navbar" class="fixed w-full z-50 transition-all duration-300 py-5 bg-transparent">
  <div class="container mx-auto px-6 flex justify-between items-center">
    
    <!-- Logo -->
    <a href="#" class="flex items-center gap-2 group">
      <img id="navbar-logo" src="logotipo.png" alt="Brand Logo"
           class="h-10 w-auto object-contain filter-white transition-all duration-300">
    </a>

    <!-- Desktop Menu -->
    <div class="hidden md:flex items-center space-x-8">
      <a href="#inicio" class="nav-link text-sm font-medium text-gray-200 hover:text-green-600 transition-colors">Inicio</a>
      <a href="#servicios" class="nav-link text-sm font-medium text-gray-200 hover:text-green-600 transition-colors">Servicios</a>
      <a href="#nosotros" class="nav-link text-sm font-medium text-gray-200 hover:text-green-600 transition-colors">Nosotros</a>
      <a href="#contacto" id="cta-button"
         class="px-5 py-2.5 rounded-full text-sm font-semibold transition-all shadow-md transform hover:-translate-y-0.5 bg-white text-green-900 hover:bg-gray-100">
        Agendar Café Virtual
      </a>
    </div>

    <!-- Mobile Menu Button -->
    <button id="mobile-menu-btn" class="md:hidden focus:outline-none text-white">
      <i data-lucide="menu" class="w-7 h-7"></i>
    </button>
  </div>

  <!-- Mobile Menu Dropdown -->
  <div id="mobile-menu" class="hidden md:hidden absolute top-full left-0 w-full bg-white shadow-xl border-t border-gray-100 flex flex-col p-6 space-y-4 animate-fadeIn">
    <a href="#inicio" class="mobile-link text-gray-800 font-medium py-2 hover:text-green-700 border-b border-gray-50">Inicio</a>
    <!-- More links -->
  </div>
</nav>
```

**JavaScript Logic:**
```javascript
const navbar = document.getElementById('navbar');
const navbarLogo = document.getElementById('navbar-logo');
const navLinks = document.querySelectorAll('.nav-link');
const ctaButton = document.getElementById('cta-button');

function updateNavbar() {
  if (window.scrollY > 50) {
    // Scrolled state
    navbar.classList.add('bg-white', 'shadow-md', 'py-3');
    navbar.classList.remove('bg-transparent', 'py-5');
    
    navLinks.forEach(link => {
      link.classList.remove('text-gray-200');
      link.classList.add('text-gray-700');
    });
    
    ctaButton.classList.remove('bg-white', 'text-green-900');
    ctaButton.classList.add('bg-green-900', 'text-white', 'hover:bg-green-800');
    
    if (navbarLogo) navbarLogo.classList.remove('filter-white');
  } else {
    // Top state (transparent)
    navbar.classList.remove('bg-white', 'shadow-md', 'py-3');
    navbar.classList.add('bg-transparent', 'py-5');
    
    navLinks.forEach(link => {
      link.classList.add('text-gray-200');
      link.classList.remove('text-gray-700');
    });
    
    ctaButton.classList.add('bg-white', 'text-green-900');
    ctaButton.classList.remove('bg-green-900', 'text-white');
    
    if (navbarLogo) navbarLogo.classList.add('filter-white');
  }
}

window.addEventListener('scroll', updateNavbar);
updateNavbar();
```

**CSS for Logo Filter:**
```css
.filter-white {
  filter: brightness(0) invert(1);
}
```

### 2. Hero Section (Full-Screen, Image Overlay)

**Features:**
- Full viewport height with background image
- Multi-layer gradient overlay
- Noise texture for depth
- Responsive typography
- Dual CTA buttons
- Scroll indicator

**Structure:**
```html
<header id="inicio" class="relative h-screen min-h-[700px] flex items-center justify-center overflow-hidden">
  <!-- Background with Overlays -->
  <div class="absolute inset-0 z-0">
    <img src="https://images.unsplash.com/photo-1451187580459-43490279c0fa?q=80&w=2072" 
         alt="Hero Background" class="w-full h-full object-cover">
    
    <!-- Gradient Overlay -->
    <div class="absolute inset-0 bg-gradient-to-r from-green-950/90 via-green-900/60 to-green-900/20 mix-blend-multiply"></div>
    
    <!-- Noise Texture -->
    <div class="absolute inset-0 opacity-10 mix-blend-overlay" 
         style="background-image: url('https://grainy-gradients.vercel.app/noise.svg');"></div>
  </div>

  <!-- Content -->
  <div class="container mx-auto px-6 relative z-10 pt-32 md:pt-40">
    <div class="max-w-3xl">
      <h1 class="text-3xl md:text-6xl font-bold text-white leading-tight mb-6">
        Evolución cloud con propósito: <br class="hidden md:block" />
        <span class="text-green-400">mejoramos tus procesos</span> con soluciones colaborativas
      </h1>
      
      <p class="text-lg md:text-xl text-gray-200 mb-8 leading-relaxed max-w-2xl">
        Ayudamos a medianas empresas a optimizar sus procesos en <strong class="text-white">la nube</strong>.
      </p>
      
      <!-- CTAs -->
      <div class="flex flex-col sm:flex-row gap-4">
        <a href="#contacto" class="flex items-center justify-center gap-2 px-8 py-4 bg-green-500 hover:bg-green-400 text-green-950 font-bold rounded-lg transition-all transform hover:scale-105 shadow-[0_0_20px_rgba(74,222,128,0.3)]">
          <i data-lucide="coffee" class="w-5 h-5"></i>
          Agendar un café virtual
        </a>
        <a href="#servicios" class="flex items-center justify-center px-8 py-4 bg-transparent border border-white/30 hover:bg-white/10 text-white font-semibold rounded-lg transition-all backdrop-blur-sm">
          Conocer servicios
        </a>
      </div>
      
      <p class="mt-8 text-sm text-gray-400 max-w-lg border-l-2 border-green-500 pl-4">
        "No solo migramos infraestructura; transferimos conocimiento para que tu equipo sea autónomo."
      </p>
    </div>
  </div>

  <!-- Scroll Indicator -->
  <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce text-white/50">
    <i data-lucide="arrow-right" class="w-6 h-6 rotate-90"></i>
  </div>
</header>
```

### 3. Service Cards

**Features:**
- Hover lift effect
- Icon color transition
- Consistent spacing
- Glassmorphic subtle borders

**Card Structure:**
```html
<div class="bg-white p-8 rounded-2xl shadow-sm border border-gray-100 hover:shadow-xl hover:-translate-y-2 transition-all duration-300 group">
  <!-- Icon Container -->
  <div class="w-14 h-14 bg-green-50 rounded-xl flex items-center justify-center text-green-700 mb-6 group-hover:bg-green-900 group-hover:text-green-400 transition-colors">
    <i data-lucide="cloud" class="w-7 h-7"></i>
  </div>
  
  <h3 class="text-xl font-bold text-gray-900 mb-3">Nube Colaborativa</h3>
  <p class="text-gray-600 text-sm leading-relaxed">
    Implementamos Google Workspace y Microsoft 365 para transformar la productividad.
  </p>
</div>
```

### 4. Contact Form (Formspree Integration)

**Features:**
- AJAX submission (no page reload)
- Success/error states
- Loading spinner
- Responsive layout with split design

**Structure:**
```html
<section id="contacto" class="py-24 bg-gray-50">
  <div class="container mx-auto px-6">
    <div class="bg-white rounded-3xl shadow-xl overflow-hidden flex flex-col md:flex-row">
      
      <!-- Left: Contact Info (5/12 width) -->
      <div class="md:w-5/12 bg-green-900 p-10 md:p-14 text-white">
        <h3 class="text-2xl md:text-3xl font-bold mb-6">¿Hablemos sobre el próximo paso?</h3>
        <p class="text-green-100 mb-8">Completa el formulario y nos contactaremos en 24 horas.</p>
        
        <div class="space-y-4 text-green-50">
          <div class="flex items-center gap-3">
            <i data-lucide="map-pin" class="text-green-400 w-5 h-5"></i>
            <span>Santiago, Chile</span>
          </div>
          <div class="flex items-center gap-3">
            <i data-lucide="mail" class="text-green-400 w-5 h-5"></i>
            <span>contacto@cystec.global</span>
          </div>
        </div>
      </div>
      
      <!-- Right: Form (7/12 width) -->
      <div class="md:w-7/12 p-10 md:p-14">
        <form id="contact-form" class="space-y-6">
          <div class="grid md:grid-cols-2 gap-6">
            <div>
              <label class="block text-sm font-medium text-gray-700 mb-2">Nombre</label>
              <input type="text" name="nombre" required 
                     class="w-full px-4 py-3 rounded-lg bg-gray-50 border border-gray-200 focus:border-green-500 focus:ring-2 focus:ring-green-200 outline-none transition-all">
            </div>
            <div>
              <label class="block text-sm font-medium text-gray-700 mb-2">Empresa</label>
              <input type="text" name="empresa" required class="w-full px-4 py-3 rounded-lg bg-gray-50 border border-gray-200 focus:border-green-500 focus:ring-2 focus:ring-green-200 outline-none transition-all">
            </div>
          </div>
          
          <div>
            <label class="block text-sm font-medium text-gray-700 mb-2">Email Corporativo</label>
            <input type="email" name="email" required class="w-full px-4 py-3 rounded-lg bg-gray-50 border border-gray-200 focus:border-green-500 focus:ring-2 focus:ring-green-200 outline-none transition-all">
          </div>
          
          <div>
            <label class="block text-sm font-medium text-gray-700 mb-2">¿Cómo podemos ayudarte?</label>
            <textarea rows="4" name="mensaje" required class="w-full px-4 py-3 rounded-lg bg-gray-50 border border-gray-200 focus:border-green-500 focus:ring-2 focus:ring-green-200 outline-none transition-all resize-none"></textarea>
          </div>
          
          <button type="submit" class="w-full py-4 bg-green-800 hover:bg-green-700 text-white font-bold rounded-lg shadow-lg hover:shadow-xl transform hover:-translate-y-1 transition-all flex items-center justify-center gap-2">
            <span>Enviar Solicitud</span>
            <i data-lucide="chevron-right" class="w-5 h-5"></i>
          </button>
        </form>
      </div>
      
    </div>
  </div>
</section>
```

**Formspree JavaScript:**
```javascript
const FORMSPREE_ENDPOINT = 'https://formspree.io/f/YOUR_FORM_ID';
const form = document.getElementById('contact-form');
const submitBtn = document.getElementById('submit-btn');

form.addEventListener('submit', async function(e) {
  e.preventDefault();
  
  submitBtn.disabled = true;
  submitBtn.innerHTML = `
    <i data-lucide="loader-2" class="w-5 h-5 animate-spin"></i>
    <span>Enviando...</span>
  `;
  lucide.createIcons();
  
  const formData = new FormData(form);
  const data = Object.fromEntries(formData.entries());
  
  try {
    const response = await fetch(FORMSPREE_ENDPOINT, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(data)
    });
    
    if (response.ok) {
      // Show success message
      formContainer.classList.add('hidden');
      successMessage.classList.remove('hidden');
      form.reset();
    }
  } catch (error) {
    // Show error
    errorMessage.classList.remove('hidden');
  } finally {
    submitBtn.disabled = false;
    submitBtn.innerHTML = originalBtnContent;
    lucide.createIcons();
  }
});
```

## 🎭 Animations & Effects

### Fade-In Animation
```css
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fadeIn {
  animation: fadeIn 0.3s ease-out forwards;
}
```

### Hover Effects
```html
<!-- Button Lift -->
<button class="transform hover:-translate-y-1 transition-all">

<!-- Card Lift with Shadow -->
<div class="hover:shadow-xl hover:-translate-y-2 transition-all duration-300">

<!-- Scale on Hover -->
<a class="transform hover:scale-105 transition-all">

<!-- Glow Effect (CTAs) -->
<a class="shadow-[0_0_20px_rgba(74,222,128,0.3)]">
```

## 🔤 Typography

### Font Stack
```css
body {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', 
               Roboto, 'Helvetica Neue', Arial, sans-serif;
}
```

### Text Sizing
```
Headings:
- Hero H1: text-3xl md:text-6xl (mobile/desktop)
- Section H2: text-3xl md:text-4xl
- Card H3: text-xl
- Subheadings: text-lg md:text-xl

Body:
- Primary: text-base (16px default)
- Small: text-sm (14px)
- Muted: text-gray-600
```

### Font Weights
```
font-bold (700) - Headings, CTAs
font-semibold (600) - Subheadings, important text
font-medium (500) - Navigation links
font-normal (400) - Body text
```

## 🖼️ Image & Media Guidelines

### Logo Handling
- **Format**: PNG with transparency
- **Placement**: `logotipo.png` in root
- **Navbar Size**: `h-10` (40px height)
- **Filter for Dark Backgrounds**: Use `.filter-white` class

### Hero Images
- **Source**: Unsplash tech/cloud imagery
- **Dimensions**: 2000px+ width for sharp display
- **Treatment**: Gradient overlay + noise texture for depth

### Icons
- **Library**: Lucide Icons (`https://unpkg.com/lucide@latest`)
- **Initialization**: `lucide.createIcons()` after DOM loads
- **Sizes**: `w-5 h-5` (small), `w-7 h-7` (medium), `w-10 h-10` (large)

## 📋 Implementation Checklist

When creating a new site with this branding:

### Setup
- [ ] Include Tailwind CSS CDN
- [ ] Add custom green palette to Tailwind config
- [ ] Include Lucide icons library
- [ ] Add custom animations CSS
- [ ] Set `scroll-behavior: smooth` on html

### Components to Build
- [ ] Fixed navigation bar with scroll behavior
- [ ] Hero section with image overlay
- [ ] Service cards grid (4 columns)
- [ ] About/Philosophy section
- [ ] Results/Benefits section (dark green background)
- [ ] Contact form with Formspree
- [ ] Footer with branding

### Required JavaScript
- [ ] Navbar scroll detection
- [ ] Mobile menu toggle
- [ ] Form AJAX submission
- [ ] Lucide icons initialization
- [ ] Dynamic year in footer

### Content Guidelines
- [ ] Use cloud/collaboration terminology
- [ ] Emphasize "transformation" and "autonomy"
- [ ] Include nature/universe metaphors in philosophy
- [ ] Highlight Chile/Cono Sur regional focus

## 🚀 Quick Start Template

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Project Name - Cloud Solutions</title>
  
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  
  <!-- Tailwind Config -->
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            green: {
              50: '#f0fdf4', 100: '#dcfce7', 200: '#bbf7d0',
              300: '#86efac', 400: '#4ade80', 500: '#22c55e',
              600: '#16a34a', 700: '#15803d', 800: '#166534',
              900: '#14532d', 950: '#052e16',
            }
          }
        }
      }
    }
  </script>
  
  <!-- Lucide Icons -->
  <script src="https://unpkg.com/lucide@latest"></script>
  
  <style>
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(-10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .animate-fadeIn { animation: fadeIn 0.3s ease-out forwards; }
    html { scroll-behavior: smooth; }
    .filter-white { filter: brightness(0) invert(1); }
  </style>
</head>

<body class="font-sans text-gray-800 antialiased selection:bg-green-900 selection:text-white">
  
  <!-- Your components here -->
  
  <script>
    lucide.createIcons();
    // Your JavaScript here
  </script>
</body>
</html>
```

## 🔧 Technology Stack

- **CSS Framework**: Tailwind CSS (CDN)
- **Icons**: Lucide Icons
- **Form Backend**: Formspree
- **Language**: Vanilla HTML/CSS/JavaScript
- **Build Tool**: Python minification script (optional)

## 📝 Notes

- Always use `container mx-auto px-6` for content wrapping
- Maintain 24-unit (96px) vertical spacing between sections
- Test mobile responsiveness at breakpoints: 768px (md), 1024px (lg)
- Use semantic HTML5 elements (`<header>`, `<section>`, `<nav>`, `<footer>`)
- Ensure all interactive elements have unique IDs for testing
- Prefer subtle animations (0.3s ease-out) over dramatic ones
