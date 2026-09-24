# Portafolio de Ilustraciones - Guía para Agregar Proyectos

## Quick Start

```bash
hugo server
# Abre http://localhost:1313
```

## Agregar un Nuevo Proyecto

### 1. Crear carpeta del proyecto
```bash
mkdir -p content/nombre-proyecto
cd content/nombre-proyecto
```

### 2. Crear `index.md` con imagen featured

**¿Cuál es la imagen principal del proyecto?**
- Esta imagen aparecerá en la página principal como tarjeta destacada
- Elige la imagen más impactante que represente el proyecto

**Estructura:**
```yaml
---
title: "Nombre del Proyecto"
date: 2024-09-24T00:00:00Z
description: "Descripción breve"
categories: ["ilustración", "categoria1", "categoria2"]
params:
  featured: true
resources:
  - src: nombre-imagen-principal.jpg
    params:
      cover: true
---

Descripción opcional del proyecto.
```

### 3. Copiar imágenes
Coloca todas las imágenes `.jpg` en `content/nombre-proyecto/`

### 4. Ejemplo
```yaml
---
title: "Khaleesi"
date: 2024-09-24T00:00:00Z
description: "Colección de ilustraciones digitales"
categories: ["ilustración", "fantasy", "personajes", "digital"]
params:
  featured: true
resources:
  - src: 707913493_18326225860280151_295781610082851128_n.jpg
    params:
      cover: true
---
```

## Categorías Recomendadas

```
Estilo: digital, tradicional, acuarela, óleo
Tema: fantasy, personajes, retratos, paisajes, conceptart
Tipo: ilustración, cómic, diseño, 3d
Año: 2024, 2023, 2022
```

## Debugear

### Ver cambios en tiempo real
```bash
hugo server
# Recarga automática
```

### Problemas comunes

**Imágenes no aparecen:**
- Verifica nombres exactos (case-sensitive): `imagen.jpg` ≠ `imagen.JPG`
- Recarga con Cmd+Shift+R
- Verifica que el archivo existe: `ls content/proyecto-nombre/*.jpg`

**Cambios no se ven:**
- Cambios en YAML requieren recarga manual
- Limpia caché del navegador (Cmd+Shift+R)

**Ver errores:**
- Mira la terminal donde corre `hugo server`
- Busca líneas con "ERROR" o "WARN"

## Documentación

**Tema Gallery (Hugo):**
https://github.com/nicokaiser/hugo-theme-gallery

**Hugo Resources:**
- [Hugo Documentation](https://gohugo.io/documentation/)
- [Image Processing](https://gohugo.io/content-management/image-processing/)
- [Taxonomies/Categories](https://gohugo.io/content-management/taxonomies/)

## Puntos Importantes

**HACER (DO):**
- Usa categorías descriptivas (múltiples por proyecto)
- Comprime imágenes antes de agregar (TinyJPG, ImageOptim)
- Haz commits después de cada proyecto nuevo
- Verifica estructura con `hugo server`

**NO HACER (DON'T):**
- Modifiques `themes/gallery/` directamente (usa `_custom.scss`)
- Agregues archivos muy grandes (>2MB por proyecto)
- Cambies `hugo.toml` sin saber qué haces

## Checklist para Nuevo Proyecto

- [ ] Carpeta en `content/nombre-proyecto/`
- [ ] `index.md` con metadatos
- [ ] Imagen principal con `cover: true`
- [ ] Categorías descriptivas
- [ ] Todas las imágenes copiadas
- [ ] Probado con `hugo server`
- [ ] Commit en Git

## Revertir Cambios

```bash
git status                          # Ver cambios
git checkout -- content/proyecto/   # Deshacer
git reset --hard HEAD               # Revertir todo
```

## Optimización

- Featured images: 400px ancho, calidad 80%
- Aspect ratio: Natural (sin distorsión)
- Tamaño objetivo: ~50-100KB por imagen featured
