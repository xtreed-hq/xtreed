# Xtreed Embed Offer

Aplicación para incrustar una oferta upsell en cualquier plataforma web.

## 📋 Tabla de Contenidos

- [Xtreed Embed Offer](#xtreed-embed-offer)
  - [📋 Tabla de Contenidos](#-tabla-de-contenidos)
  - [🚀 Cómo obtener el código de integración](#-cómo-obtener-el-código-de-integración)
  - [💻 Instalación](#-instalación)
  - [🐛 Modo Debug](#-modo-debug)
  - [🎨 Personalización](#-personalización)
    - [Estilos del Card](#estilos-del-card)
    - [Fuente Personalizada](#fuente-personalizada)
    - [Cambio de Textos](#cambio-de-textos)
  - [📝 Parámetros](#-parámetros)
    - [Obligatorios](#obligatorios)
    - [Opcionales](#opcionales)
  - [💡 Ejemplos](#-ejemplos)
    - [Ejemplo Básico](#ejemplo-básico)
    - [Ejemplo con Personalización](#ejemplo-con-personalización)
    - [Ejemplo con Estilos Avanzados](#ejemplo-con-estilos-avanzados)
  - [📞 Soporte](#-soporte)

## 🚀 Cómo obtener el código de integración

1. En tu cuenta conectada en Xtreed, ve a **Productos**
2. Crea o selecciona un producto
3. Accede a **Estrategias de ventas**
4. Crea o visualiza una estrategia como **Upsell**
5. Ve al campo **Código para integración** y copia el código
6. Pega el código donde quieras que aparezca en tu sitio

## 💻 Instalación

Con el código en mano, pégalo donde quieras que aparezca en tu sitio:

```html
<div id="xtreed-root" 
     data-language="pt" 
     data-offer-id="123" 
     data-item-id="456" 
     data-environment="production">
</div>
```

## 🐛 Modo Debug

Para facilitar la integración, tenemos el modo debug que imprime `console.log` de la queryString, parámetros pasados en `xtreed-root` y algunos otros datos importantes.

**Para activar:**
```html
data-debug="true"
```

⚠️ **Atención:** ¡Desactívalo cuando vayas a producción!

## 🎨 Personalización

### Estilos del Card

Utilizamos [xstyled](https://xstyled.dev) para hacer todo el manejo de UI. Ya tenemos algunos estilos base pero pueden ser alterados según sea necesario. Ve la documentación: [https://xstyled.dev/docs/utility-props/](https://xstyled.dev/docs/utility-props/)

**Sintaxis de estilos:** Los estilos deben ser pasados como JSON usando la sintaxis de `@xstyled/styled-components` con propiedades abreviadas y valores del sistema de design tokens.

**Ejemplos de sintaxis:**
- `padding: 24px` → `{"p": 6}`
- `margin: 16px` → `{"m": 4}`
- `background: #ffffff` → `{"bg": "white"}`
- `color: #1a202c` → `{"color": "gray.800"}`
- `font-size: 18px` → `{"fontSize": "18px"}`
- `border-radius: 8px` → `{"borderRadius": "8px"}`

Todas las secciones del card son personalizables (excepto las estructurales), y pueden ser pasadas como parámetros en el código de integración:

| Parámetro | Descripción | Ejemplo |
|-----------|-------------|---------|
| `data-container-style` | Estilos del contenedor principal, borde, background, padding, etc. | `'{"border": "2px solid gray.200", "borderRadius": "12px", "p": 6, "bg": "white"}'` |
| `data-image-wrapper-style` | Estilos del wrapper de la imagen, tamaño, etc. | `'{"w": "100%", "h": "200px", "overflow": "hidden", "borderRadius": "8px"}'` |
| `data-image-style` | Estilos y propiedades de la imagen del producto | `'{"w": "100%", "h": "100%", "objectFit": "cover"}'` |
| `data-message-error-style` | Estilos del mensaje de error | `'{"color": "red.500", "fontSize": "14px", "p": 3}'` |
| `data-message-success-style` | Estilos del mensaje de éxito | `'{"color": "green.500", "fontSize": "14px", "p": 3}'` |
| `data-product-meta-style` | Estilos del contenedor donde se mostrarán los metadatos del producto | `'{"py": 4, "px": 6}'` |
| `data-product-name-style` | Estilos del texto del nombre del producto | `'{"fontSize": "20px", "fontWeight": 700, "color": "gray.800"}'` |
| `data-product-description-style` | Estilos del texto de la descripción del producto | `'{"fontSize": "14px", "color": "gray.600", "lineHeight": 1.5}'` |
| `data-product-price-style` | Estilos del precio del producto | `'{"fontSize": "18px", "fontWeight": 600, "color": "green.600"}'` |
| `data-product-price-without-discount-style` | Estilos del precio sin descuento del producto (si lo hay) | `'{"fontSize": "14px", "color": "gray.500", "textDecoration": "line-through"}'` |
| `data-accept-button-style` | Estilos del botón de aceptar oferta | `'{"bg": "green.500", "color": "white", "px": 6, "py": 3, "borderRadius": "8px"}'` |
| `data-reject-button-style` | Estilos del botón de rechazar oferta | `'{"bg": "transparent", "color": "gray.500", "border": "1px solid gray.200", "px": 6, "py": 3}'` |

### Fuente Personalizada

Para agregar una fuente personalizada, agrega las siguientes propiedades:

```html
data-custom-font-url="https://fonts.googleapis.com/css2?family=Bitcount+Single+Ink:wght@100..900&display=swap"
data-custom-font-name="Bitcount Single Ink"
```

- `data-custom-font-url`: URL del stylesheet de la fuente (ej: Google Fonts)
- `data-custom-font-name`: Nombre de la fuente personalizada (ej: "Bitcount Single Ink")

### Cambio de Textos

Para cambiar los textos de los botones, agrega las siguientes propiedades:

⚠️ **Atención:** Es necesario agregar en los 3 idiomas de la plataforma (pt, es, en)

```html
data-accept-button-text='{"pt": "Aceitar oferta", "es": "Aceptar oferta", "en": "Accept offer"}'
data-reject-button-text='{"pt": "Recusar oferta", "es": "Rechazar oferta", "en": "Reject offer"}'
```

## 📝 Parámetros

### Obligatorios

| Parámetro | Descripción | Ejemplo |
|-----------|-------------|---------|
| `id="xtreed-root"` | **Obligatorio** - Referencia donde inicializar la integración (no puede ser cambiado) | `id="xtreed-root"` |
| `data-language` | Idioma actual del panel Xtreed | `pt`, `en` o `es` |
| `data-offer-id` | ID de la oferta ofrecida (obtenido en el panel Xtreed) | `"123"` |
| `data-item-id` | ID de la estrategia de ventas (obtenido en el panel Xtreed) | `"456"` |
| `data-environment` | Ambiente de la integración | `development` o `production` |

### Opcionales

| Parámetro | Descripción | Por defecto |
|-----------|-------------|-------------|
| `data-debug` | Activa logs de debug en la consola | `false` |
| `data-custom-font-url` | URL de la fuente personalizada | - |
| `data-custom-font-name` | Nombre de la fuente personalizada | - |
| `data-accept-button-text` | Texto del botón de aceptar (JSON con idiomas) | - |
| `data-reject-button-text` | Texto del botón de rechazar (JSON con idiomas) | - |

## 💡 Ejemplos

### Ejemplo Básico

```html
<div id="xtreed-root" 
     data-language="pt" 
     data-offer-id="123" 
     data-item-id="456" 
     data-environment="production">
</div>
```

### Ejemplo con Personalización

```html
<div id="xtreed-root" 
     data-language="pt" 
     data-offer-id="123" 
     data-item-id="456" 
     data-environment="production"
     data-debug="true"
     data-custom-font-url="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap"
     data-custom-font-name="Inter"
     data-container-style='{"border": "2px solid gray.200", "borderRadius": "12px", "p": 6, "bg": "white"}'
     data-product-name-style='{"fontSize": "24px", "fontWeight": 600, "color": "gray.800"}'
     data-accept-button-style='{"bg": "green.500", "color": "white", "px": 6, "py": 3, "borderRadius": "8px", "border": "none"}'
     data-accept-button-text='{"pt": "Aceitar oferta", "es": "Aceptar oferta", "en": "Accept offer"}'
     data-reject-button-text='{"pt": "Recusar oferta", "es": "Rechazar oferta", "en": "Reject offer"}'>
</div>
```

### Ejemplo con Estilos Avanzados

```html
<div id="xtreed-root" 
     data-language="pt" 
     data-offer-id="123" 
     data-item-id="456" 
     data-environment="production"
     data-container-style='{"maxWidth": "400px", "mx": "auto", "boxShadow": "0 4px 6px rgba(0, 0, 0, 0.1)"}'
     data-image-wrapper-style='{"w": "100%", "h": "200px", "overflow": "hidden", "borderRadius": "8px"}'
     data-image-style='{"w": "100%", "h": "100%", "objectFit": "cover"}'
     data-product-meta-style='{"py": 4}'
     data-product-name-style='{"fontSize": "20px", "fontWeight": 700, "mb": 2, "color": "gray.700"}'
     data-product-description-style='{"fontSize": "14px", "color": "gray.500", "lineHeight": 1.5, "mb": 4}'
     data-product-price-style='{"fontSize": "18px", "fontWeight": 600, "color": "green.600"}'
     data-accept-button-style='{"w": "100%", "bg": "linear-gradient(135deg, blue.500 0%, purple.600 100%)", "color": "white", "py": 3.5, "borderRadius": "8px", "border": "none", "fontWeight": 600, "cursor": "pointer"}'
     data-reject-button-style='{"w": "100%", "bg": "transparent", "color": "gray.500", "py": 3.5, "border": "1px solid gray.200", "borderRadius": "8px", "mt": 2, "cursor": "pointer"}'>
</div>
```

## 📞 Soporte

Para dudas o soporte, contacta a través del panel Xtreed o consulta la documentación oficial.
