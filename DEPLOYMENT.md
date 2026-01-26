# Sistema de Automatización de Despliegue
# =======================================

Este proyecto incluye un pipeline de construcción y despliegue automatizado para tu sitio estático.

## 🚀 Scripts Disponibles

### 1. `build_site.py` - Pipeline de Construcción
Ejecuta el proceso de minificación y optimización.

```bash
python3 build_site.py
```

**Funcionalidades:**
- ✅ Backup automático con timestamp
- ✅ Minificación inteligente (preserva anclajes `<!-- CONTENT -->`)
- ✅ Optimización de scripts con `defer`
- ✅ Reporte de métricas (tamaño, ahorro)

---

### 2. `deploy.py` - Despliegue Automático
Ejecuta build + deploy en un solo comando.

```bash
# Preview local (servidor HTTP en puerto 8000)
python3 deploy.py --target preview

# Deploy a GitHub Pages
python3 deploy.py --target github-pages

# Deploy a Netlify
python3 deploy.py --target netlify
```

---

## 🔧 Configuración de Automatización

### Opción A: Git Hook (Recomendado para desarrollo local)

Automáticamente ejecuta el build antes de cada commit.

**Instalación:**
```bash
chmod +x .githooks/pre-commit
git config core.hooksPath .githooks
```

**Uso:**
Ahora cada vez que hagas `git commit`, el build se ejecutará automáticamente.

---

### Opción B: GitHub Actions (Recomendado para CI/CD)

Pipeline automatizado en la nube que se ejecuta con cada push.

**Configuración:**
1. El archivo `.github/workflows/deploy.yml` ya está creado
2. Haz push de estos cambios:
   ```bash
   git add .github/
   git commit -m "feat: add CI/CD pipeline"
   git push
   ```

3. **Para GitHub Pages:**
   - Ve a: `Settings` > `Pages`
   - Source: `Deploy from a branch`
   - Branch: `gh-pages` / `root`
   - Guarda

4. **Para Netlify:**
   - Añade secrets en GitHub:
     - `NETLIFY_AUTH_TOKEN`
     - `NETLIFY_SITE_ID`
   - Descomenta la sección de Netlify en `deploy.yml`

---

## 📋 Workflow Recomendado

### Desarrollo Local:
```bash
# 1. Edita index.html
# 2. Preview local
python3 deploy.py --target preview

# 3. Commit (auto-build con git hook)
git add .
git commit -m "feat: nueva sección"
git push
```

### Despliegue a Producción:
```bash
# Opción manual
python3 deploy.py --target github-pages

# Opción automática (push a main)
git push origin main  # GitHub Actions se encarga del deploy
```

---

## 🎯 Estructura de Archivos

```
ancla/
├── index.html              # Archivo fuente
├── index.min.html          # Versión optimizada (generada)
├── build_site.py           # Pipeline de construcción
├── deploy.py               # Script de despliegue
├── backups/                # Backups automáticos
│   └── index_YYYYMMDD_HHMMSS.html
├── .githooks/              # Git hooks
│   └── pre-commit          # Hook de pre-commit
└── .github/
    └── workflows/
        └── deploy.yml      # GitHub Actions workflow
```

---

## 🔍 Troubleshooting

### Error: "No se encuentra build_site.py"
```bash
# Asegúrate de estar en el directorio correcto
cd /home/jet/cystec/ancla
```

### Error: "Permission denied" en git hook
```bash
chmod +x .githooks/pre-commit
```

### GitHub Pages no actualiza
```bash
# Forzar deploy manual
python3 deploy.py --target github-pages
```

### Netlify CLI no encontrado
```bash
npm install -g netlify-cli
netlify login
```

---

## 💡 Tips Pro

1. **Ignorar archivos generados en Git:**
   ```bash
   echo "index.min.html" >> .gitignore
   ```

2. **Ver diferencias antes de deploy:**
   ```bash
   diff index.html backups/index_*.html | less
   ```

3. **Rollback rápido:**
   ```bash
   # Ver backups disponibles
   ls -lah backups/
   
   # Restaurar un backup específico
   cp backups/index_20260125_224012.html index.html
   ```

---

## 📊 Métricas Actuales

- **Tamaño original:** 32 KB
- **Tamaño optimizado:** 22 KB  
- **Ahorro:** ~30%
- **Anclajes protegidos:** `<!-- CONTENT -->`
- **Scripts optimizados:** `defer` añadido automáticamente

---

¡Tu pipeline de despliegue está listo para producción! 🚀
