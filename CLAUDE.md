# Documentación del Proyecto Isaju

## 📋 Descripción General

**Isaju** es una tienda en línea de peluches artesanales construida con Astro. El sitio web presenta una colección de peluches hechos a mano con un diseño moderno y acogedor. El proyecto utiliza Astro 5.9.3 como framework principal.

### Propósito
- Mostrar productos (peluches) en una galería
- Permitir ver detalles de productos individuales
- Facilitar contacto a través de WhatsApp
- Presentar una marca artesanal con identidad visual única

---

## 🏗️ Arquitectura del Proyecto

### Stack Tecnológico
- **Framework**: Astro 5.9.3
- **Lenguaje**: TypeScript (configuración estricta)
- **Estilos**: CSS Modules
- **Tipo de Proyecto**: Static Site Generation (SSG)

### Estructura de Directorios

```
isaju-astro/
├── public/                    # Assets estáticos
│   ├── fonts/                 # Fuente personalizada "DK Magical Brush"
│   ├── *.jpg                  # Imágenes de productos
│   ├── logo.png               # Logo de la marca
│   └── favicon.svg            # Favicon
├── src/
│   ├── components/            # Componentes reutilizables
│   │   ├── content/           # Contenedor de contenido
│   │   ├── footer/            # Pie de página
│   │   ├── header/            # Encabezado con logo
│   │   ├── product-card/      # Tarjeta de producto
│   │   └── whatsaap/          # Botón flotante de WhatsApp
│   ├── icons/                 # Iconos SVG
│   │   └── whatsapp.svg
│   ├── layouts/               # Layouts de página
│   │   └── app-layout.astro   # Layout principal
│   └── pages/                 # Páginas del sitio
│       ├── index.astro        # Página principal
│       └── product/
│           └── [id]/          # Página dinámica de producto
├── astro.config.mjs           # Configuración de Astro
├── global.css                 # Estilos globales
├── package.json               # Dependencias y scripts
└── tsconfig.json              # Configuración de TypeScript
```

---

## 🧩 Componentes Principales

### 1. **AppLayout** (`src/layouts/app-layout.astro`)
Layout principal que envuelve todas las páginas. Incluye:
- Header con logo
- Contenedor de contenido principal
- Botón flotante de WhatsApp
- Footer

### 2. **Header** (`src/components/header/index.astro`)
Encabezado del sitio con:
- Logo clickeable que redirige a la página principal
- Estilos personalizados con CSS Modules

### 3. **Footer** (`src/components/footer/index.astro`)
Pie de página con:
- Copyright: "Isaju Copyright 2025"

### 4. **ProductCard** (`src/components/product-card/index.astro`)
Tarjeta de producto que muestra:
- Imagen del producto
- Nombre del producto (hardcodeado: "Peluche Cafe")
- Precio (hardcodeado: $60)
- Enlace a la página de detalle del producto

**Props:**
- `image`: Ruta de la imagen del producto

**Nota**: Actualmente todos los productos redirigen a `/product/1` y tienen información hardcodeada.

### 5. **Whatsapp** (`src/components/whatsaap/index.astro`)
Botón flotante de WhatsApp que:
- Muestra el icono de WhatsApp
- Enlaza a: `https://wa.me/573218524293`
- Se abre en nueva pestaña

### 6. **Content** (`src/components/content/index.astro`)
Componente contenedor que envuelve el contenido principal usando slots.

---

## 📄 Páginas

### 1. **Página Principal** (`src/pages/index.astro`)
- **Ruta**: `/`
- **Contenido**:
  - Título: "Fabrica de peluches hechos con amor"
  - Subtítulo: "Tienda"
  - Descripción: "Aquí es donde puedes ver los productos en esta tienda."
  - Galería de 6 productos:
    - `/peluche.jpg`
    - `/perro.jpg`
    - `/peluche-blanco.jpg`
    - `/oso-cafe.jpg`
    - `/cerdo.jpg`
    - `/monster.jpg`

### 2. **Página de Producto** (`src/pages/product/[id]/index.astro`)
- **Ruta**: `/product/[id]` (ruta dinámica)
- **Funcionalidad**:
  - Usa `getStaticPaths()` para generar rutas estáticas
  - Actualmente solo genera la ruta para `id: 1`
- **Contenido**:
  - Imagen del producto (hardcodeada: `/peluche-blanco.jpg`)
  - Nombre: "Peluche Cafe"
  - Precio: "$60.000"
  - Descripción: "descripcion especifica del producto" (placeholder)

**Nota**: La página de producto tiene información hardcodeada y solo soporta un producto.

---

## 🎨 Estilos y Diseño

### Fuente Personalizada
El proyecto utiliza la fuente **"DK Magical Brush"** ubicada en `/public/fonts/DK Magical Brush.otf`. Esta fuente se aplica a todos los títulos (h1-h6) y le da un aspecto artesanal y acogedor al sitio.

### Variables CSS Globales
```css
--font-family: 'DK Magical Brush', Arial, sans-serif
```

### Color Principal
- Color de texto: `#18243E` (azul oscuro)
- Color de fondo: `rgba(244, 242, 239)` (beige claro)

### Estilos
- Todos los componentes usan **CSS Modules** para estilos encapsulados
- Estilos globales definidos en `global.css`
- Diseño responsive (viewport configurado)

---

## 🚀 Comandos Disponibles

```bash
# Desarrollo local
npm run dev          # Inicia servidor de desarrollo en localhost:4321

# Producción
npm run build        # Construye el sitio para producción en ./dist/
npm run preview      # Previsualiza la build localmente

# Utilidades
npm run astro        # Ejecuta comandos CLI de Astro
```

---

## 📦 Dependencias

```json
{
  "astro": "^5.9.3"
}
```

El proyecto es minimalista y solo depende de Astro, sin dependencias adicionales.

---

## 🔧 Configuración

### Astro Config (`astro.config.mjs`)
Configuración básica sin integraciones adicionales.

### TypeScript Config (`tsconfig.json`)
- Extiende la configuración estricta de Astro
- Incluye tipos de Astro automáticamente
- Excluye el directorio `dist`

---

## 📝 Notas de Desarrollo

### Áreas de Mejora Identificadas

1. **Datos Hardcodeados**:
   - Los productos tienen información hardcodeada (nombre, precio, descripción)
   - Todos los productos redirigen a `/product/1`
   - Solo existe una página de producto generada

2. **Sugerencias de Implementación**:
   - Crear un sistema de datos (JSON, CMS, o base de datos) para productos
   - Implementar `getStaticPaths()` completo para generar todas las páginas de productos
   - Hacer que `ProductCard` reciba props dinámicas (nombre, precio, id)
   - Agregar más productos y páginas dinámicas

3. **Funcionalidades Potenciales**:
   - Sistema de carrito de compras
   - Integración con pasarela de pagos
   - Galería de imágenes en página de producto
   - Búsqueda y filtrado de productos
   - Categorías de productos

---

## 🖼️ Assets

### Imágenes de Productos
- `peluche.jpg`
- `perro.jpg`
- `peluche-blanco.jpg`
- `oso-cafe.jpg`
- `cerdo.jpg`
- `monster.jpg`
- `teddie.jpg` (no utilizado actualmente)

### Logo
- `logo.png` - Logo principal de la marca
- `logo.jpg` - Versión alternativa (no utilizada)

### Fuentes
- `DK Magical Brush.otf` - Fuente personalizada para títulos

---

## 📞 Información de Contacto

- **WhatsApp**: +57 321 852 4293
- **Enlace directo**: `https://wa.me/573218524293`

---

## 🎯 Propósito del Negocio

Isaju es una fábrica de peluches artesanales que se enfoca en productos hechos con amor. El sitio web sirve como catálogo digital y punto de contacto para clientes interesados en sus productos.

---

## 📚 Recursos Adicionales

- [Documentación de Astro](https://docs.astro.build)
- [Astro Discord](https://astro.build/chat)

---

**Última actualización**: Generado automáticamente mediante análisis del proyecto
**Versión del proyecto**: 0.0.1

