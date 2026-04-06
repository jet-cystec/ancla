# cystec.global
![Preview del sitio](image.png)

**Cystec Global** — Consultoría estratégica para soluciones cloud desde el sur del mundo.

---

## 🚀 Tecnologías
- HTML5 semántico
- CSS3 — Tailwind CSS (compilado local, sin CDN)
- JavaScript vanilla
- Lucide Icons (local, v0.400.0)
- Formspree (formulario de contacto AJAX)

---

## 📂 Estructura de Archivos
| Archivo | Descripción |
|---|---|
| `index.html` | Página principal (Landing Page) |
| `politica-privacidad.html` | Página dedicada de Política de Privacidad |
| `assets/css/tailwind-compiled.css` | Tailwind CSS compilado localmente |
| `assets/js/lucide.min.js` | Iconos Lucide (local) |
| `hero-bg.webp` | Imagen de fondo del Hero |
| `logotipo.webp` | Logo de la marca |

---

## 📋 Changelog

### v1.2
- **fix:** Hero section — cambio de `h-screen` a `min-h-screen` para evitar recorte de contenido en viewports de escritorio cortos. Ver [#pitfalls](#⚠️-pitfalls-conocidos).
- **feat:** Migración de Política de Privacidad a página independiente (`politica-privacidad.html`) para mejorar la UX de la Landing Page.
- **style:** Eliminación del texto `v1.1 (Minified)` del footer.
- **style:** Enlace "Términos de Servicio" oculto en el footer hasta que el contenido esté listo.

### v1.1
- **feat:** Implementación de sección de Política de Privacidad con acordeón HTML5 nativo (`<details>` / `<summary>`).
- **feat:** Actualización del footer con links legales.

### v1.0
- Lanzamiento inicial del sitio.

---

## ⚠️ Pitfalls Conocidos

### Hero con `h-screen` + `overflow-hidden` recorta contenido
**Síntoma:** El texto ubicado al final del hero (la cita en cursiva) no se veía en monitores de escritorio con menor altura de viewport, pero sí en móvil.

**Causa:** La combinación de `h-screen` (altura fija igual al viewport) con `overflow-hidden` en el `<header>` hace que cualquier contenido que supere ese alto quede recortado. En móvil, el texto es más compacto y no desborda.

**Solución:** Reemplazar `h-screen` por `min-h-screen`. Esto garantiza que el hero ocupe como mínimo toda la pantalla, pero puede crecer si el contenido lo necesita.

```diff
- <header class="relative h-screen min-h-[700px] flex items-center justify-center overflow-hidden">
+ <header class="relative min-h-screen min-h-[700px] flex items-center justify-center overflow-hidden">
```

---

## 📩 Contacto
- **Email:** [contacto@cystec.global](mailto:contacto@cystec.global)
- **Web:** [www.cystec.global](https://www.cystec.global)

---
*© 2026 Cystec Global.*
