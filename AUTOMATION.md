# 🚀 Sistema de Automatización Completo

## 📊 Arquitectura del Pipeline

```mermaid
graph TB
    A[👨‍💻 Desarrollador edita index.html] --> B{Método de Deploy}
    
    B -->|Opción 1: Local| C[python3 deploy.py --target preview]
    B -->|Opción 2: Git| D[git commit]
    B -->|Opción 3: CI/CD| E[git push]
    
    C --> F[build_site.py]
    D --> G[Pre-commit Hook]
    E --> H[GitHub Actions]
    
    G --> F
    H --> F
    
    F --> I[1️⃣ Crear Backup]
    I --> J[2️⃣ Minificar HTML]
    J --> K[3️⃣ Optimizar Scripts]
    K --> L[4️⃣ Generar index.min.html]
    
    L --> M{Método Deploy}
    
    M -->|Preview| N[localhost:8000]
    M -->|GitHub Pages| O[gh-pages branch]
    M -->|Netlify| P[Netlify CDN]
    
    O --> Q[🌐 Sitio en Producción]
    P --> Q
    
    style A fill:#e1f5fe
    style F fill:#fff3e0
    style L fill:#e8f5e9
    style Q fill:#f3e5f5
```

## 🎯 Flujos de Trabajo

### Flujo 1: Desarrollo Local
```mermaid
sequenceDiagram
    participant Dev as Desarrollador
    participant Script as deploy.py
    participant Build as build_site.py
    participant Server as HTTP Server
    
    Dev->>Script: python3 deploy.py --target preview
    Script->>Build: Ejecuta build pipeline
    Build->>Build: Crea backup
    Build->>Build: Minifica HTML
    Build->>Build: Optimiza scripts
    Build-->>Script: ✅ index.min.html
    Script->>Server: Inicia servidor :8000
    Server-->>Dev: 🌐 http://localhost:8000
```

### Flujo 2: Deploy con Git Hook
```mermaid
sequenceDiagram
    participant Dev as Desarrollador
    participant Git as Git
    participant Hook as Pre-commit Hook
    participant Build as build_site.py
    
    Dev->>Git: git commit -m "feat: nueva sección"
    Git->>Hook: Ejecuta .githooks/pre-commit
    Hook->>Build: python3 build_site.py
    Build->>Build: Pipeline completo
    Build-->>Hook: ✅ Éxito
    Hook->>Git: git add index.min.html
    Git-->>Dev: ✅ Commit creado
```

### Flujo 3: CI/CD Automático
```mermaid
sequenceDiagram
    participant Dev as Desarrollador
    participant GitHub as GitHub
    participant Actions as GitHub Actions
    participant Build as build_site.py
    participant Pages as GitHub Pages
    
    Dev->>GitHub: git push origin main
    GitHub->>Actions: Trigger workflow
    Actions->>Build: python3 build_site.py
    Build-->>Actions: ✅ Artifact
    Actions->>Pages: Deploy a gh-pages
    Pages-->>Dev: 🌐 https://user.github.io/repo
```

## 📁 Estructura del Proyecto

```
ancla/
├── 🛠️ SCRIPTS DE AUTOMATIZACIÓN
│   ├── build_site.py          # Pipeline de construcción
│   ├── deploy.py              # Gestor de despliegue
│   └── DEPLOYMENT.md          # Documentación completa
│
├── ⚙️ CONFIGURACIÓN GIT
│   ├── .githooks/
│   │   └── pre-commit         # Hook automático
│   ├── .github/
│   │   └── workflows/
│   │       └── deploy.yml     # CI/CD Pipeline
│   └── .gitignore             # Archivos ignorados
│
├── 📄 ARCHIVOS DEL SITIO
│   ├── index.html             # Fuente original
│   ├── index.min.html         # Versión optimizada (generada)
│   ├── *.png                  # Assets
│   └── README.md
│
└── 📦 BACKUPS
    └── backups/
        └── index_YYYYMMDD_HHMMSS.html
```

## 🎮 Comandos Rápidos

| Acción | Comando | Descripción |
|--------|---------|-------------|
| **Build** | `python3 build_site.py` | Solo construir (sin deploy) |
| **Preview** | `python3 deploy.py --target preview` | Build + servidor local |
| **GitHub Pages** | `python3 deploy.py --target github-pages` | Build + deploy a GH Pages |
| **Netlify** | `python3 deploy.py --target netlify` | Build + deploy a Netlify |
| **Activar Hook** | `git config core.hooksPath .githooks` | Auto-build en cada commit |

## 🔧 Próximos Pasos

### Paso 1: Configurar Git Hook (Opcional)
```bash
git config core.hooksPath .githooks
```
✅ Ahora cada commit ejecutará automáticamente el build.

### Paso 2: Probar Preview Local
```bash
python3 deploy.py --target preview
# Navega a: http://localhost:8000
```

### Paso 3: Configurar GitHub Pages
```bash
# Push de los archivos de configuración
git add .github/ .githooks/ build_site.py deploy.py .gitignore DEPLOYMENT.md
git commit -m "feat: add deployment automation"
git push

# Luego en GitHub:
# Settings > Pages > Source: gh-pages branch
```

### Paso 4: (Opcional) Netlify
```bash
# Instalar CLI
npm install -g netlify-cli

# Login
netlify login

# Deploy
python3 deploy.py --target netlify
```

---

**¡Tu sistema de automatización está completamente configurado!** 🎉
