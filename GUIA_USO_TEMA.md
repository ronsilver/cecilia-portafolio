# Guía de Uso - Tema Gallery Hugo

## Estructura del Proyecto

Tu portafolio usa el tema **hugo-theme-gallery**, un tema minimalista para galerías de fotos. La estructura funciona así:

```
content/
├── _index.md              ← Página principal
├── category1/             ← Carpeta con categoría
│   ├── _index.md          ← Info de la categoría
│   ├── album1/            ← Álbum individual
│   │   ├── index.md       ← Info del álbum
│   │   ├── photo1.jpg     ← Fotos
│   │   ├── photo2.jpg
│   │   └── cover.jpg      ← Imagen portada (opcional)
│   └── album2/
│       ├── index.md
│       └── *.jpg
```

## Cómo Crear un Álbum

### 1. Crear la estructura de carpetas
```bash
content/illustrations/portfolio-2024/
├── index.md
├── illustration1.jpg
├── illustration2.jpg
└── cover.jpg
```

### 2. Escribir el archivo `index.md`
```yaml
---
title: "Portafolio 2024"
date: 2024-09-24
description: "Colección de ilustraciones digitales 2024"
categories: ["portafolio"]
resources:
  - src: cover.jpg
    params:
      cover: true
---

Descripción adicional del álbum aquí (markdown).
```

## Opciones Principales

### Front Matter (metadatos)

| Opción | Descripción | Ejemplo |
|--------|-------------|---------|
| `title` | Nombre del álbum | `title: "Mis Ilustraciones"` |
| `date` | Fecha (ordena de nuevo→viejo) | `date: 2024-09-24` |
| `description` | Texto descriptivo | `description: "Obras del 2024"` |
| `categories` | Categorías para agrupar | `categories: ["arte", "digital"]` |
| `weight` | Orden manual (menor = primero) | `weight: 10` |

### Parámetros especiales

```yaml
params:
  featured: true          # Destacar en homepage
  private: true           # Ocultar de listas (seguirá en featured)
  sort_by: "Date"         # Ordenar por: Name o Date
  sort_order: "desc"      # asc o desc
```

### Portada personalizada

```yaml
resources:
  - src: cover.jpg
    params:
      cover: true         # Esta imagen es la portada
      hidden: true        # No mostrar en galería (solo portada)
```

## Estructura Recomendada para Cecilia

```
content/
├── _index.md                    ← Inicio
├── categories/
│   ├── ilustraciones/_index.md
│   ├── designs/_index.md
│   └── animations/_index.md
├── ilustraciones/
│   ├── _index.md
│   ├── 2024/
│   │   ├── index.md
│   │   ├── cover.jpg
│   │   └── *.jpg
│   └── 2023/
│       ├── index.md
│       └── *.jpg
├── designs/
│   ├── _index.md
│   └── proyecto1/
│       ├── index.md
│       └── *.jpg
└── about.md                     ← Info personal
```

## Notas Importantes

⚠️ **NO USAR WebP** - Tienen un bug de renderizado en Hugo
- Usar: JPG, PNG
- NO: WebP

✅ **Metadatos de imágenes** - Títulos en lightbox desde:
1. Tag EXIF `ImageDescription` (Lightroom, exiftool)
2. Front matter `resources[].title`

```bash
# Agregar titulo EXIF con exiftool
exiftool -ImageDescription="Descripción de la foto" foto.jpg
```

✅ **Ordenar por peso personalizado**:
```yaml
resources:
  - src: foto1.jpg
    params:
      weight: 30
  - src: foto2.jpg
    params:
      weight: 20  # Aparece primero (menor peso = primero)
```

## Social Icons (Redes Sociales)

Agrega esto en `hugo.toml`:
```toml
[params.socialIcons]
  instagram = "https://instagram.com/tuusuario"
  email = "mailto:contacto@ejemplo.com"
  behance = "https://behance.net/tuusuario"
```

Iconos disponibles: facebook, instagram, github, youtube, email, linkedin, etc.

## Personalización

### Cambiar URL de portada de sitio
Edita en `hugo.toml`:
```toml
baseURL = 'https://tudominio.com/'  # Cambiar aquí
```

### Colores personalizados
Crea `assets/css/custom.css` con tus estilos CSS.

### JavaScript personalizado
Crea `assets/js/custom.js` con tu código.

## Construir y Previsualizar

```bash
# Previsualizar en desarrollo
hugo server -D

# Compilar para producción
hugo
```

El sitio compilado estará en la carpeta `public/`.

## Recursos

- [Tema Gallery en GitHub](https://github.com/nicokaiser/hugo-theme-gallery)
- [Demo oficial](https://nicokaiser.github.io/hugo-theme-gallery/)
- [Example Site](https://github.com/nicokaiser/hugo-theme-gallery/tree/main/exampleSite)
