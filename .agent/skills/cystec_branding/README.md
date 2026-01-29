# Cystec Branding - Quick Reference

## Placeholders in Template

Replace these placeholders in `landing-page-template.html`:

### Brand Identity
- `{{PROJECT_NAME}}` - Your project name
- `{{BRAND_NAME}}` - Brand name for footer
- `{{COMPANY_NAME}}` - Legal company name
- `{{TAGLINE}}` - Brand tagline/motto

### Navigation
- `{{CTA_TEXT}}` - Call-to-action button text (e.g., "Agendar Café Virtual")

### Hero Section
- `{{HERO_IMAGE_URL}}` - Unsplash or custom hero background URL
- `{{HERO_TITLE}}` - Main hero heading (first part)
- `{{HERO_HIGHLIGHT}}` - Highlighted text (green color)
- `{{HERO_SUBTITLE}}` - Hero heading continuation
- `{{HERO_DESCRIPTION}}` - Subheading paragraph
- `{{PRIMARY_CTA}}` - Primary button text
- `{{SECONDARY_CTA}}` - Secondary button text
- `{{QUOTE}}` - Inspirational quote

### Services
- `{{SERVICES_TITLE}}` - Services section title
- `{{SERVICES_SUBTITLE}}` - Services section subtitle
- Add service cards by duplicating the card structure

### Contact
- `{{CONTACT_TITLE}}` - Contact section heading
- `{{CONTACT_DESCRIPTION}}` - Contact intro text
- `{{LOCATION}}` - Your location
- `{{EMAIL}}` - Contact email
- `{{FORM_TITLE}}` - Form heading
- `{{FORM_SUBTITLE}}` - Form description

### Formspree Setup
1. Create account at https://formspree.io
2. Create a new form
3. Replace `YOUR_FORM_ID` in the JavaScript with your actual Form ID

## Color Quick Reference

```html
<!-- Backgrounds -->
bg-green-900   <!-- Dark sections -->
bg-green-50    <!-- Light accents -->
bg-gray-50     <!-- Section backgrounds -->

<!-- Text -->
text-green-900   <!-- Dark headings -->
text-green-400   <!-- Bright highlights -->
text-gray-600    <!-- Body text -->

<!-- Buttons -->
bg-green-500 hover:bg-green-400   <!-- Primary CTA -->
bg-green-800 hover:bg-green-700   <!-- Secondary CTA -->
```

## Icon Usage (Lucide)

Common icons used:
- `cloud` - Cloud services
- `shield-check` - Security
- `users` - Teams/collaboration
- `cpu` - Technology/processes
- `coffee` - Meeting/consultation
- `mail` - Email contact
- `map-pin` - Location
- `menu` - Mobile menu
- `arrow-right` - Navigation
- `check-circle` - Success states
- `loader-2` - Loading spinner

Usage:
```html
<i data-lucide="icon-name" class="w-5 h-5"></i>
```

Remember to call `lucide.createIcons()` after dynamically adding icons!

## Responsive Breakpoints

- `sm:` - 640px
- `md:` - 768px (tablets)
- `lg:` - 1024px (desktop)
- `xl:` - 1280px
- `2xl:` - 1536px

## Common Patterns

### Hover Lift Effect
```html
<div class="hover:-translate-y-2 transition-all duration-300">
```

### Button with Icon
```html
<button class="flex items-center justify-center gap-2">
  <i data-lucide="icon-name" class="w-5 h-5"></i>
  <span>Text</span>
</button>
```

### Service Card Grid
```html
<div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
  <!-- Cards -->
</div>
```

### Section Divider
```html
<div class="w-20 h-1 bg-green-500 mx-auto mt-6 rounded-full"></div>
```
